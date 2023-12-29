# Quantum
Quantum 是一款基于golang开发的综合漏洞扫描工具,目前支持存活检测、端口扫描、服务检测、未授权检测、弱口令检测、ms1710检测、web指纹识别.

** 为什么选择它 **

- 支持检测并发,速度更快;
- 支持基础协议识别,检测更高效;
- 支持登陆验证,结果更准确;
- 支持debug模式,调试更方便;
- 支持结果汇总,更省力;
## 免责声明

该工具仅用于安全自查检测.

由于传播、利用此工具所提供的信息而造成的任何直接或者间接的后果及损失，均由使用者本人负责，作者不为此承担任何责任.

本人拥有对此工具的修改和解释权。未经网络安全部门及相关部门允许，不得善自使用本工具进行任何攻击活动，不得以任何方式将其用于商业目的.  
  
## 快速使用
[](https://github.com/outmansec/Quantum/assets/61048948/7c380e4a-c751-4abe-9b82-33580dd0b094)


  

  
## 命令参数

|  参数   |                             含义                             |
| :-----: | :----------------------------------------------------------: |
|    t    | 设置扫描目标格式如下:192.168.0.1;192.168.0.1,192.168.0.2;192.168.0.1-255;192.168.0.1-192.168.0.255;192.168.0.1/24; |
|    f    | 如ip.txt,文本每行一个,格式参照-t |
|    m    |     设置扫描模式目前支持alive、portscan、servicescan、brute、ms17010、webfinger、all    |
|    p    |     设置扫描端口;不设置使用默认配置格式如下1-65535;22,23      |
|  user   |  设置弱口令检测用户名;不设置使用默认配置如:admin、root,admin   |
|   pwd   |  设置弱口令检测密码;不设置使用默认配置如:123456、123456,admin  |
|  userf  |                    设置弱口令检测用户名列表如user.txt每行一个                   |
|  pwdf   |                    设置弱口令检测列表如pwd.txt每行一个                      |
|  rate   |   设置IP并发数量默认为600;服务检测、弱口令检测模块为设置并发数/10    |
|    c    |              设置弱口令检测单IP并发数量默认为4;              |
| timeout |                         设置超时时间默认为3000                         |
|    v    |                      验证检测结果                      |
| prefix  |     设置一个关键词根据内置模版生成更多口令如huawei,h3c等     |
|   np    |                          不检测存活                          |
|   o    |           保存扫描结果默保存格式为xlsx           |
|   debug    |           显示调试信息           |
|   log    |           保存日志如:-log text,支持text和json格式   |

## 支持那些服务检测

| 序号 | 默认端口 | 默认协议 |
| :------: | :------: | :------: |
|1|    21    |   FTP    |
|2|    22    |   SSH    |
|3|    23    |  Telnet  |
|4|    80    |   http   |
|5|   139    | Netbios  |
|6|   443    |  Https   |
|7|   445    |   smb    |
|8|   1433   |  Mssql   |
|9|   1521   |  Oracle  |
|10|   3306   |  Mysql   |
|11|   3389   |   rdp    |
|12|   5432   | postgres |
|13|   6379   |  redis   |
|14|  27017   | mongodb  |
## 支持那些未授权检测
| 序号 | 默认端口 | 默认协议 | 是否支持验证 | 验证方法 |
| :------: | :------: | :------: | :------: | -------- |
|1|    21    |   FTP    | 是 | 目录信息 |
|2|    23    |  Telnet  | 是 | 登陆信息 |
|3|  4445   | smb  | 是 | 目录信息 |
|4|   6379   |  redis   | 是 | info信息 |
|5|  27017   | mongodb  | 是 | 版本信息 |

## 支持那些弱口令检测
| 序号 | 默认端口 | 默认协议 | 是否支持验证 | 验证方法 |
| :------: | :------: | :------: | :------: | -------- |
|1|    21    |   FTP    | 是 | 目录信息 |
|2|    22    |   SSH    | 是 | 执行命令 |
|3|    23    |  Telnet  | 是 | 登陆信息 |
|4|   445    |   smb    | 是 | 目录信息 |
|5|   1433   |  Mssql   | 是 | 版本信息 |
|6|   1521   |  Oracle  | 是 | 版本信息 |
|7|   3306   |  Mysql   | 是 | 版本信息 |
|8|   3389   |   rdp    | 否 | 不支持 |
|9|   5432   | postgres | 是 | 版本信息 |
|10|   6379   |  redis   | 是 | info信息 |
|11|  27017   | mongodb  | 是 | 版本信息 |

## 支持那些web指纹检测

内置EHole规则

规则详情查看

https://github.com/EdgeSecurityTeam/EHole/blob/main/finger.json

## 更新日志

**0.8.2**

1. 优化弱口令检测模块;
   
**0.8.1**
1. 添加smb未授权检测支持;

**0.8.0**

1. 添加端口扫描调试信息打印支持;
2. 添加ms171010检测调试信息打印支持;
3. 优化ms17010检测规则;

**0.7.9**

1. 修复postgres协议识别问题;
   
**0.7.8**

1. 优化日志保存支持text和json格式;
   
**0.7.7**

1. 添加ssh登陆弱算法支持;
2. 添加ssh登陆弱密钥交换算法支持;
3. 添加mongodb(3.6<版本)登陆支持;
4. 修复mongodb登陆特殊字符问题;
   
**0.7.6**

1. 修复多端口内存泄漏问题;
   
**0.7.5**

1. 修复h3c无法爆破问题;
2. 修改默认超时为3000毫秒;

**0.7.4**

1. 支持使用更低的系统版本;
   
**0.7.3**

1. 修复windows下GC回收问题;
2. 优化windows颜色显示问题;
3. 优化debug选项;
4. 删除bt参数;
   
**0.7.2**

1. 独立ms17010检查,防止触发告警;
   
**0.7.1**

1. 优化指纹识别请求错误问题;

**0.7.0**

1. 优化https协议识别;
2. 新增webfinger、all模式;

**0.6.0**

1. 新增ms17010检测;
   
**0.5.0**

1. 新增日志保存;
2. 新增调试信息打印;

**0.4.0**

1. 添加telent未授权漏洞;
2. 优化telnet弱口令,为满足大部分telnet登陆,并发限制为1;

**0.3.0**

1. 修复ssh登陆长等待导致爆破进度无法进行问题;
2. 修复telnet误报问题,支持登陆验证;
3. 修复ftp误报问题;
4. 优化单ip并发数;

**0.2.0**

1. 修复telnet登陆长等待导致爆破进度无法进行问题
