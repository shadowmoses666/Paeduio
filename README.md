# Paeduio
Paeduio open interface RESTful API
测试脚本及软件安装使用
Postman软件安装
下载Postman

官网下载地址:https://www.getpostman.com/downloads

安装Postman（Windows系统）

运行安装程序：下载完成后，双击安装包（如.exe文件）开始安装。

遵循安装向导：按照安装向导的指示，选择安装路径（虽然默认可能是C盘，但你可以选择其他位置），同意使用条款，按需选择是否创建桌面快捷方式等。

完成安装：点击“Install”按钮进行安装。安装完成后，根据提示重启Postman或直接启动。

控制软件准备
安装PAEDUIO™ v1.1.0或以上版本控制软件。

创建至少一个可用预录语音、背景音乐或紧急广播。

创建一个用于API测试的管理员账号。

数据准备
加密狗序列号

服务器IP地址

管理员账号和密码

Postman准备
启动Postman

创建或选择一个workspace

导入测试脚本

菜单 → File → Import → files → 选择 PAEDUIO_Postman_API_Testcase_Collection.json

导入测试环境变量

菜单 → File → Import → files → 选择 PAEDUIO_Postman_Environment.json

选择环境变量

左侧菜单栏 → Environments → PAEDUIO™测试环境 → 勾选"Set active"

修改环境变量

左侧菜单栏 → Environments → 选择"PAEDUIO™测试环境"

将"数据准备"中数据填入对应变量的"Current value", 并save保存

Variable

说明

ip

服务器IP地址

secretkey

加密狗序列号

username

管理员账号

password

管理员密码

Important
脚本执行过程中，将在Globals中生成临时变量，临时变量不需要手动修改。
测试脚本每一个使用说明
左侧菜单栏 → Collections → PAEDUIO™ API Test Case

选择需要测试的接口，点击"Send"按钮执行测试

测试用例
登录
测试用例将使用所提供的管理员账号和密码进行登录，登录成功后返回token，后续接口需要使用token进行鉴权。

所有其他接口的前置操作

返回结果示例：

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjbGllbnRUeXBlIjoiYXBpIiwiaXNEZXYiOmZhbHNlLCJhY2NvdW50IjoiYWRtaW4iLCJ0aW1lc3RhbXAiOjE3MjM1MzUyNjg2MzF9.8502l_ugpJdZQmrJ6tJSxstYRf_l0d_jO1VxPSKvz0A",
        "freshToken": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJjbGllbnRUeXBlIjoiYXBpIiwiZXhwIjoxNzI2MTI3MjY4LCJhY2NvdW50IjoiYWRtaW4ifQ.40765rcc27Re8vRebIvrG_aHuWxR_--XVkB_RG6FIpA",
        "expires": 900
    },
    "timestamp": 1723535268670
}
查询分区组信息
测试用例查询控制软件中已建立的分区组信息

将查询得到的第一个分区组ID作为变量groupID进行保存，后续接口需要使用groupID进行分区组操作

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": [
        {
            "id": 579103178612805,
            "name": "1"
        }
    ],
    "timestamp": 1723535424252,
    "totalCount": 1,
    "pageSize": 1,
    "currPage": 1,
    "totalPage": 1
}
查询分区信息
测试用例查询控制软件中的分区信息

将查询得到的第一个分区ID作为变量DeviceId进行保存，后续接口需要使用DeviceId进行分区操作

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": [
        {
            "id": "150-015-08394-20221213-00140",
            "name": "PRP-IM2C1A"
        }
    ],
    "timestamp": 1723535457633,
    "totalCount": 1,
    "pageSize": 1,
    "currPage": 1,
    "totalPage": 1
}
查询分区详情
测试用例查询控制软件中第一个分区的详细信息，包括音量、是否故障、是否忙碌等

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": {
        "fault": false,
        "busy": false,
        "volume": 0,
        "id": "150-015-08394-20221213-00140",
        "name": "PRP-IM2C1A"
    },
    "timestamp": 1723535583038
}
设置分区音量
测试用例将查询到的第一个分区的音量设置为50

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": null,
    "timestamp": 1727161891550
}
查询预设任务
测试用例查询控制软件中已预设的任务信息

将查询得到的第一个任务ID作为变量taskID进行保存，后续接口需要使用taskID进行任务操作

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": [
        {
            "id": 579103922839621,
            "name": "测试任务",
            "type": 1
        }
    ],
    "timestamp": 1723535751236,
    "totalCount": 1,
    "pageSize": 1,
    "currPage": 1,
    "totalPage": 1
}
开始广播
测试用例将启动查询得到的第一个预设任务

将得到的广播ID作为变量broadcastID进行保存，后续接口需要使用broadcastID进行广播操作

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": 579172963225669,
    "timestamp": 1723536051464
}
停止广播
测试用例将“开始广播”接口启动的预设任务

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": null,
    "timestamp": 1723536133807
}
获取系统
测试用例获取系统状态，包括是否故障、是否忙碌等

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": {
        "fault": false,
        "evac": false
    },
    "timestamp": 1723536180807
}
刷新token
测试用例刷新token，保持登录状态

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": {
        "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJjbGllbnRUeXBlIjoiYXBpIiwiYWNjb3VudCI6ImFkbWluIn0.43bmepjxLDW6lDf2IxZi5nAvu7DQCa61GfqBPXs12KY",
        "freshToken": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJjbGllbnRUeXBlIjoiYXBpIiwiZXhwIjoxNzI2MTI4NDEzLCJhY2NvdW50IjoiYWRtaW4ifQ.ZGfQIOC043t7k2SXJw6I2Eey5IuKSndvp2z45_Eaodw",
        "expires": 900
    },
    "timestamp": 1723536413895
}
登出
测试用例登出，结束登录状态

返回结果示例

{
    "successful": true,
    "code": 200,
    "msg": "Success",
    "data": null,
    "timestamp": 1723536914947
}
Last updated 2024-09-27 15:02:52 +0800
