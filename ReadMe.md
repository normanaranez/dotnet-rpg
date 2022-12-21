# Create database on docker
```console
docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=password123!!" -p 1433:1433 --name TYPICALAPI_MSSQL_SERVER_2019 --hostname TYPICALAPI_MSSQL_SERVER_2019 -d mcr.microsoft.com/mssql/server:2019-latest
```

#check database location in docker
```console
docker ps -a
```

#copy existing database to mssql server using command line
```console
docker cp C:\Users\arane\Downloads\AdventureWorks2019.bak TYPICALAPI_MSSQL_SERVER_2019:/var/opt/mssql/
```

#create gitignore file for dotnet
```console
dotnet new gitignore
```

#create generate models and dbcontext from database
```console
dotnet ef dbcontext scaffold "Server=localhost,1433;Database=DatabaseName;User Id=sa;Password=password123!!;TrustServerCertificate=true;" Microsoft.EntityFrameworkCore.SqlServer -o Models --context-namespace AppDbContext --context-dir Data --force
```

#create generate models and dbcontext from database without OnConfiguring
```console
dotnet ef dbcontext scaffold "Server=localhost,1433;Database=DatabaseName;User Id=sa;Password=password123!!;TrustServerCertificate=true;" Microsoft.EntityFrameworkCore.SqlServer -o Models --context-namespace AppDbContext --context-dir Data --no-onconfiguring --force
```