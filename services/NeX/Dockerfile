FROM mcr.microsoft.com/dotnet/sdk:7.0 AS Builder

WORKDIR /nex/src

COPY . .

RUN dotnet publish . -p:PublishTrimmed=true -p:PublishSingleFile=true -p:DebugType=None -r linux-x64 --self-contained -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:7.0

WORKDIR /nex/server

COPY --from=Builder /nex/src/out .

ENTRYPOINT [ "/nex/server/nex" ]
