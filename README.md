<h1 align="center"> 阿里巴巴开放平台SDK </h1>

<p align="center"> .</p>


## Installing

```shell
$ composer require liaosp/ali_open -vvv
```

## Usage
场景： 拉取阿里巴巴商家的采购数据，同步到erp上，采用的是多用户模式

```php
        $obj = new \JavaReact\AlibabaOpen\AliOpen(['page'=>1]);
        $obj->setAppkey('你的appkey');
        $obj->setAppsecret('你的秘钥');
        $obj->setAccessToken('自己想办法去获取token，如果设置的是多用户单用户的直接复制，应用管理中的token');
        $res =$obj->order->setApi('com.alibaba.trade:alibaba.trade.getBuyerOrderList-1')->get(); //api 就是阿里巴巴文档中的
        var_dump($res);
```

项目中可以继承他：

````php
<?php


namespace App\Services\AliOpen;


class AliOpen extends \JavaReact\AlibabaOpen\AliOpen
{
    public function __construct($params = array())
    {
        $this->setAppkey('39376**');
        $this->setAppsecret('0RsvFZYV**');
        $this->access_token = '06410386-242c-41f6-8a20-5e7e0d2b6229';
        parent::__construct($params);
    }
}

````

获取订单列表的例子 
```php
        $get_data =( new AliOpen([     //这边的AliOpen ,是你设置appkey的对象
            'page'=>1,
            'pageSize'=>100,
        ]))
            ->order
            ->setApi('com.alibaba.trade:alibaba.trade.getBuyerOrderList-1')
            ->get();
```
获取订单详情的例子 
```php
        $get_data = (new AliOpen([
            'webSite'=>1688,
            'orderId'=>$this->app->order_id,
        ]))
            ->order
            ->setApi('com.alibaba.trade:alibaba.trade.get.buyerView-1')
            ->get();

```

更新日志：

## License

MIT
