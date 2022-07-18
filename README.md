# photoapi
搭建自己的随机图API

# 具体可以前往我的博客:tonywdy.github.io进行了解！

# 前言
首先，你需要了解leancloud的部署官文！
云引擎部署php：https://docs.leancloud.cn/sdk/engine/deploy/php/#%E5%AE%89%E8%A3%85%E4%BE%9D%E8%B5%96composerjson

# 正式开始

## 上传图片
将自己的图片上传至图床，这里以gitlub图床为例
在gitlub中创建一个专门用于图床的公开仓库，将图片上传至仓库中
![](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718184252.png)

# 注意将图片按照一定规律命名，例如 2.jpg，以便于后序接口实现

## 配置仓库
创建一个仓库```photoapi```
注意⚠️一定要设置为```公告```
![](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718184420.png)

### 新建一个```composer.json```
填写:
```json
{
  "php": "8.0"
}
```

### 新建一个```public/index.php```
填写内容：
```php
<?php
//初始化随机数生成器种子，这行代码也可以删除
$seed = time();
//获取随机数
$num = rand(1,45);
//拼接图片地址
$picpath = "https://gitlab.com/KINGWDY/photoapi/raw/main/".$num.".png";
//重定位到图片
die(header("Location: $picpath"));
?>
```
> 这里的```$picpath = ``` 后改为你自己的链接！

## 部署到leancloud
新建一个应用：
![](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718184749.png) 

切换到```云引擎\web\部署```
![](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718184830.png)

![点击部署](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718184923.png)

填入你仓库的git链接
或者换我的：
![](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718185008.png)

然后配置分支为main，点击部署
![](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718185057.png)

日志：
![](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718185147.png)

然后就可以看到：
![](https://gitlab.com/KINGWDY/photoapi/-/raw/main/20220718185250.png)

# 完成✅！
