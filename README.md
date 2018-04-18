##协程 HTTP 客户端

#### 简介

提供可以在协程模式下工作的非阻塞 HTTP 请求功能。  
当前根据项目实际需要，仅提供最小化功能。  

#### 具体功能如下：
1. 只支持 GET、POST 请求；
1. 不支持文件上传；
1. 不支持 HTTPS 协议；
1. 不支持 gzip、deflate 等内容编码；
1. 不支持 COOKIE；
1. 不支持认证机制；

#### 使用方式：
API 参照 guzzlehttp 设计，不过不支持其中部分选项。  
Example 1:
```php
include __DIR__."/../vendor/autoload.php";

use lanzhi\http\Client;
use Symfony\Component\Console\Output\ConsoleOutput;
use Symfony\Component\Console\Logger\ConsoleLogger;

$uri = 'test.com/get.php';

$output = new ConsoleOutput(ConsoleOutput::VERBOSITY_VERY_VERBOSE);
$client = new Client([], new ConsoleLogger($output));
$requestTask = $client->get($uri, ['query'=>$query]);

$requestTask->run();

$response = $requestTask->getReturn();
echo "response status code:", $response->getStatusCode(), "\n";
if($response->getBody()){
    echo "response body:", $response->getBody()->getContents(), "\n";
}else{
    var_dump($response);
}

```

Example 2:
```php

```
```console
modified:   src/RequestBuilder.php
```

#### 其它
。。。