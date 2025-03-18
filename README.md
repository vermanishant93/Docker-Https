# Docker with Https

# Commands
	- dotnet dev-certs https --trust: To enable https port on localhost

## In Your Project Location:
	- dotnet user-secrets set "Kestrel:Certificates:Development:Password" "reallyStrongPwd123"
	- docker build -t weatherapi .
	- docker run -p 8080:8080 weatherapi

## To enable https:
	## In Windows:

	-- dotnet dev-certs https -ep $env:USERPROFILE\.aspnet\htps\WeatherAPI.pfx -p reallyStrongPwd123
	
	-- docker run -p 8080:8080 -p 8081:443 -e ASPNETCORE_URLS="https://+;http://+" -e ASPNETCORE_HTTPS_PORT=8081 -e ASPNETCORE_ENVIRONMENT=Development -v $env:APPDATA\microsoft\UserSecrets\:/root/.microsoft/usersecrets -v $env:USERPROFILE\.aspnet\https:/root/.aspnet/https/ weatherapi

	## Mac:
	-- dotnet dev-certs https -ep "$HOME/.aspnet/https/WeatherAPI.pfx" -p reallyStrongPwd123
	
	-- docker run -p 8080:8080 -p 8081:443 \
	  -e ASPNETCORE_URLS="https://+;http://+" \
	  -e ASPNETCORE_HTTPS_PORT=8081 \
	  -e ASPNETCORE_ENVIRONMENT=Development \
	  -v "$HOME/.microsoft/usersecrets:/root/.microsoft/usersecrets:ro" \
	  -v "$HOME/.aspnet/https:/root/.aspnet/https:ro" \ weatherapi
