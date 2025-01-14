# Definitions for SDK Metrics<a name="guide_sdk-metrics-definitions"></a>

You can use the following descriptions of SDK Metrics to interpret your results\. In general, these metrics are available for review with your Technical Account Manager during regular business reviews\. AWS Support resources and your Technical Account Manager should have access to SDK Metrics data to help you resolve cases, but if you discover data that is confusing or unexpected, but doesn’t seem to be negatively impacting your applications’ performance, it is best to review that data during scheduled business reviews\.


****  

| Metric: | CallCount | 
| --- | --- | 
|  Definition  |  Total number of successful or failed API calls from your code to AWS services  | 
|  How to use it  |  Use it as a baseline to correlate with other metrics like errors or throttling\.  | 


****  

| Metric: | ClientErrorCount | 
| --- | --- | 
|  Definition  |  Number of API calls that fail with client errors \(4xx HTTP response codes\)\. *Examples: Throttling, Access denied, S3 bucket does not exist, and Invalid parameter value\.*   | 
|  How to use it  |  Except in certain cases related to throttling \(ex\. when throttling occurs due to a limit that needs to be increased\) this metric can indicate something in your application that needs to be fixed\.  | 


****  

| Metric: | ConnectionErrorCount | 
| --- | --- | 
|  Definition  |  Number of API calls that fail because of errors connecting to the service\. These can be caused by network issues between the customer application and AWS services including load balancers, DNS failures, transit providers\. In some cases, AWS issues may result in this error\.  | 
|  How to use it  |  Use this metric to determine whether issues are specific to your application or are caused by your infrastructure and/or network\. High ConnectionErrorCount could also indicate short timeout values for API calls\.  | 


****  

| Metric: | ThrottleCount | 
| --- | --- | 
|  Definition  |  Number of API calls that fail due to throttling by AWS services\.  | 
|  How to use it  |  Use this metric to assess if your application has reached throttle limits, as well as to determine the cause of retries and application latency\. Consider distributing calls over a window instead of batching your calls\.  | 


****  

| Metric: | ServerErrorCount | 
| --- | --- | 
|  Definition  |  Number of API calls that fail due to server errors \(5xx HTTP response codes\) from AWS Services\. These are typically caused by AWS services\.  | 
|  How to use it  |  Determine cause of SDK retries or latency\. This metric will not always indicate that AWS services are at fault, as some AWS teams classify latency as an HTTP 503 response\.  | 


****  

| Metric: | EndToEndLatency | 
| --- | --- | 
|  Definition  |  Total time for your application to make a call using the AWS SDK, inclusive of retries\. In other words, regardless of whether it is successful after several attempts, or as soon as a call fails due to an unretriable error\.  | 
|  How to use it  |  Determine how AWS API calls contribute to your application’s overall latency\. Higher than expected latency may be caused by issues with network, firewall, or other configuration settings, or by latency that occurs as a result of SDK retries\.  | 