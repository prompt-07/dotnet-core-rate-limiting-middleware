# dotnet-core-rate-limiting-middleware


```JSON
"IpRateLimiting": {
    "EnableEndpointRateLimiting": false,
    "StackBlockedRequests": false,
    "RealIpHeader": "X-Real-IP", //rate-limiting based on ip address
    "ClientIdHeader": "X-ClientId",
    "HttpStatusCode": 429,
    "IpWhitelist": [], // IP whitelisting mostly for test ie: locahost :  "127.0.0.1" (IPv4), "::1/10"(IPv6)
    "EndpointWhitelist": [ "get:/api/license", "*:/api/status" ], // dont block user trying to see license or some status endpoint whitelisting
    "ClientWhitelist": [ "dev-id-1", "dev-id-2" ],
    "GeneralRules": [
      {
        "Endpoint": "*",
        "Period": "1s",
        "Limit": 2
      },
      {
        "Endpoint": "*",
        "Period": "1m",
        "Limit": 100
      },
      {
        "Endpoint": "*",
        "Period": "24h",
        "Limit": 1000
      },
      {
        "Endpoint": "*",
        "Period": "7d",
        "Limit": 10000
      }
    ]
  }
}
//FILTERS : 2req per second / 100 per min / 1000 per day / 10K per week



```

![alt text](https://raw.githubusercontent.com/prompt-07/dotnet-core-rate-limiting-middleware/sada_01/ratelimiting-demo.png)
