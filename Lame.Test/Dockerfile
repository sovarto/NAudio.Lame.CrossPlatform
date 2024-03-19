#See https://aka.ms/customizecontainer to learn how to customize your debug container and how Visual Studio uses this Dockerfile to build your images for faster debugging.

FROM mcr.microsoft.com/dotnet/sdk:8.0
RUN apt-get update && apt-get install lame -y
ARG BUILD_CONFIGURATION=Release
WORKDIR /src
COPY ["Lame.Test/Lame.Test.csproj", "Lame.Test/"]
COPY ["NAudio.Lame/NAudio.Lame.csproj", "NAudio.Lame/"]
COPY ["LameDLLWrap/LameDLLWrap.csproj", "LameDLLWrap/"]
RUN dotnet restore "./Lame.Test/./Lame.Test.csproj"
COPY . .
RUN dotnet build "./Lame.Test/./Lame.Test.csproj"
WORKDIR "/src/Lame.Test"
ENTRYPOINT ["dotnet", "test", "/src/Lame.Test/Lame.Test.csproj"]
