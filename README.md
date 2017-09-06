Jenkins自动化工程更新插件篇
--------------------

> 首先进入到Jenkins服务器

> 进入到服务器的项目目录下
>> `cd 项目目录 // cd /var/lib/jenkins/workspace`

> 删除旧的node_modules文件夹
>> `rm -rf node_modules/`

> 安装依赖插件
> `yarn cnpm install`

> 打包项目
>> `npm run build yarn run build`

> 把打包好的项目文件移动到部署服务器上测试是否可行 -r 之后参数，移动的文件 多个文件空格隔开 最后是目标地址
>> `scp -r dist/module/ dist/static/ 用户名@ip:/部署地址`

> 可行之后压缩node_modules文件
>> `tar -zcvf 压缩之后的名称 要压缩的文件名`

> 把压缩好的.tar.gz文件移动到存放位置 参数 1：移动的目标文件 2： 移动的目标位置
>> `mv h5-ynd-pigRaising-mobile.tar.gz /var/node_modules`

> 删除 `node_modules` 目录  构建时会重新解压缩生成

> 删除dist目录 构建时会生成
>> ``rm -rf dist/``

> 两个目录
>> 插件压缩包：/var/node_modules/...
>> 项目目录文件：/var/lib/jenkins/workspace/...

> 完成一次插件更新操作
