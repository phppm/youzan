# support swoole 1.8.8 for youzan/zan

1. composer global require rustphp/youzan
2. 修改 src/Store/Database/Flow.php 文件

在下面的代码 中

    private $engineMap = [
        'Mysqli' => 'Zan\Framework\Store\Database\Mysql\Mysqli',
    ];

新增一行配置 
 
    Swoole_mysql'=>'com\imcjj\youzan\SwooleMysqlDriver
    
3. 修改 src/Network/Connection/ConnectionInitiator.php 文件 

在 initPool 方法中 增加下面的代码 

    case 'Swoole_mysql':
        $factory = new SwooleMysqlFactory($config);
        break;
        
4. Mysql连接配置文件中 使用


    'engine' => 'swoole_mysql'