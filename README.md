# 服务器代理服务

如果你觉得本项目对你有用,而且你也恰巧有这方面的需求,你也可以选择通过我的购买链接赞助我  
- [搬瓦工GIA服务器](https://bandwagonhost.com/aff.php?aff=41846)  - - - 仅推荐购买GIA套餐 - - -   

如果你希望购买一些现成的代理服务,可选择下述代理服务
- [搬瓦工官方机场](https://justmysocks.net/members/aff.php?aff=16884)  

# sing-sheath
<a href="./README.zh_CN.md">中文</a>|
<a href="./README.md">English</a>

A simple sing-box client that can't be simpler.

This project is powered by [sing-sword](https://github.com/zzzgydi/sing-sword) project.

## How to use

- Add an outbound
- Add an inbound. Both tun mode and mixed mode are supported. But tun mode requires admin/root privilege.
- Click restart. It will
  - add all the outbounds to a urltest outbound named **auto** .
  - add all the outbounds to a selector outbound named **selector-out** .
  - save the configuration.
  - check the configuration.
  - restart sing-box.
- Select an outbound from clash dashboard.

Remember, **every change you made requires a restart including switch on/off an inbound.**

## Reset
Click reset will reset the configuration to `sing-box-default.json` except that the outbounds are kept unchanged.

## Inbounds
Inbounds can be swiched on/off. And the default configuration for tun/mixed is read
from `sing-box-default.json`. If you want to change the default switch behavior. Change this file.

## Outbounds
Outbounds can be import from clipboard as outbound json or outbound json array.

## Core
The core is at `sing-sword/sing/core`. If the
directory doesn't exist. It will be created and a default sing-box core will be copied.

Users can add their own sing-box core of any version to core directory.

## Profile
You can select or create a profile by clicking the profile input button. By default
the created profile will be the same as current profile.

## How it works

sing-sheath is basicly a sing-box backend with a json editor. And when you click restart, sing-sheath will add a selector outbound and a urltest outbound and save the json file.

## First time start
At the first time start, it will create sing-sword directory and copy default sing-box core there. Usually, after sing-box started, geodata will be downloaded automatically. But depending on internet connectivity and GFW behavior, it might fail and leave a empty geodata database file.
In this case, remove empty geodata and add a 
reliable proxy for geodata downloading.

## FAQ

### Tun Mode

Tun mode requires privilege to run.

#### On Windows

You should run as administrator.

#### On Linux

After first run. run the following command（If failed, change * to your core name）.

```
sudo setcap cap_net_bind_service,cap_net_admin=+ep ~/.config/sing-sword/sing/core/*
```

#### On MacOS

After first run （If failed, change * to your core name）.

```
sudo chown root:admin ~/.config/sing-sword/sing/core/*
sudo chmod +sx ~/.config/sing-sword/sing/core/*
```
