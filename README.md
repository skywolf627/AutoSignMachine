# 介绍

自动签到复活版

当前只在维护 Unicom 的部分，移除了部分过期活动。

## 当前状态

每天能获得 30+ 积分以及 2.5GB+ 日流量，建议配合 [UnicomTask](https://github.com/srcrs/UnicomTask) 食用。

## 必读必读

**本 Fork 仅支持 Pull Requests 不支持任何的 Issue 以及讨论**

**本项目随时可能停止维护，但不会影响到你自己已部署项目的使用**

**本项目禁止传播，请在24小时内删除**
## 使用方法

1. 获得设备的 appid，参考该项目[UnicomTask](https://github.com/srcrs/UnicomTask#2%E5%87%86%E5%A4%87%E9%9C%80%E8%A6%81%E7%9A%84%E5%8F%82%E6%95%B0)自行获取
2. fork 本项目
3. 完善配置文件
  ```
UNICOM_USERNAME = '18812345678'
UNICOM_PASSWORD = '654321'
UNICOM_APPID = 'xxxxxx'
  ```
   - 将 18812345678 替换为你的自己的登录号码
   - 将 654321 替换为你自己的登录密码
   - 将 xxxxxx 替换为上面获取的 appid
4. 把上面的配置修改好后复制到[这里](https://www.baidufe.com/fehelper/en-decode/index.html)，然后选择【加密】中的 【Base64编码】，你会在下面的输入框中获得编码后的配置文件
5. 参考该项目[UnicomTask](https://github.com/srcrs/UnicomTask#3%E5%B0%86%E5%8F%82%E6%95%B0%E5%A1%AB%E5%88%B0secrets)，增加一个 Secrets 名为 UNICOM_CONFIG，值为第 4 步获得的编码后配置文件
6. 最后还是参考该项目 [UnicomTask](https://github.com/srcrs/UnicomTask#4%E5%BC%80%E5%90%AFactions) 运行 Github Action

## 一些说明

该项目是支持了自动调度的，也就是它会随机地在一天中完成所有任务，而不是集中到某一小段时间完成。这样可以模拟人在操作，防止屏蔽。

也就是说，你需要让本项目运行至少一天才能看出来效果（或者你可以去 Github Action 日志查看运行结果）

## Todo

下面的是现在有问题的部分功能，大佬们如果感兴趣可以修一修 🙃

- [ ] 【首页】-【游戏】-【每日打卡】-【每日任务】，脚本可以自动玩游戏，但自动领取被风控了，需要手动点击领取

#
#
#
#
#
#
#
#
#

# 以下是原项目介绍
# AutoSignMachine

**一个自动执行任务的工具，通过它可以实现账号自动签到，自动领取权益等功能，帮助我们轻松升级。**

## bilibili签到任务
**实现现B站帐号的每日自动观看、分享、投币视频，获取经验，每月自动领取会员权益等功能，帮助我们轻松升级会员到Lv6并赚取电池。**

详细功能目录如下:

* **每天自动登录，获取经验**
* **每天自动观看、分享、投币视频**
* **每天漫画自动签到**
* **每天自动直播签到，领取奖励**
* **每天自动使用直播中心银瓜子兑换B币**
* **每个月自动领取5张B币券和大会员权益**

```sh
node index.js bilibili --cookies "b6*********4a581;"
```

### docker部署
```sh
# 构建
docker build -t auto-sign-machine:latest  -f docker/Dockerfile .
# 运行
docker run \
  --name auto-sign-machine \
  -d \
  -e enable_bilibili=true \
  -e DedeUserID=41*****1073  \
  -e SESSDATA=05*********333*b1 \
  -e bili_jct=b6*********4a581 \
  auto-sign-machine:latest
```

## 52pojie签到任务
**实现现52pojie帐号的每日签到任务。**

```sh
node index.js 52pojie --htVD_2132_auth b22d**********************aNjr --htVD_2132_saltkey Jc***********I
```

### docker部署
```sh
# 构建
docker build -t auto-sign-machine:latest  -f docker/Dockerfile .
# 运行
docker run \
  --name auto-sign-machine \
  -d \
  --label traefik.enable=false \
  -e enable_52pojie=true \
  -e htVD_2132_auth=b******************jr \
  -e htVD_2132_saltkey=Jc************I \
  auto-sign-machine:latest
```
、
## iqiyi签到任务
**实现现iqiyi帐号的每日签到任务。**
详细功能目录如下:

* **普通用户每天自动获取积分**
* **vip用户每日签到随机成长值及积分**
* **vip用户每日浏览会员俱乐部+1成长值**

```sh
node index.js iqiyi --P00001 b********jr --P00PRU 12***24 --QC005 5f******6fe --dfp Jc************I
```

### docker部署
```sh
# 构建
docker build -t auto-sign-machine:latest  -f docker/Dockerfile .
# 运行
docker run \
  --name auto-sign-machine \
  -d \
  --label traefik.enable=false \
  -e enable_iqiyi=true \
  -e P00001=b********jr \
  -e P00PRU=12***24 \
  -e QC005=5f******6fe \
  -e dfp=Jc************I \
  auto-sign-machine:latest
```


、
## 联通APP签到任务
**实现现联通帐号的每日签到任务。**
详细功能目录如下:

* **每日签到积分**
* **冬奥积分活动**
* **每日定向积分**
* **每日游戏楼层宝箱**
* **每日抽奖**
* **首页-游戏-娱乐中心-沃之树**
* **首页-小说-阅读越有礼打卡赢话费**
* **首页-小说-读满10章赢好礼**
* **首页-小说-读满10章赢好礼-看视频领2积分**
* **首页-签到有礼-免流量得福利-3积分天天拿(阅读打卡)**
* **首页-小说-阅读福利抽大奖**
* **首页-签到有礼-免费领-浏览领积分**
* **首页-签到有礼-免费拿-看视频夺宝**
* **首页-签到有礼-免费抽**
* **首页-签到有礼-赚更多福利**
* **首页-游戏-娱乐中心-每日打卡**
* **每日游戏时长-天天领取3G流量包**
* **首页-积分查询-游戏任务**

```sh
node index.js unicom --user 131*******12 --password 11****11 --appid f7af****ebb
```

### docker部署
```sh
# 构建
docker build -t auto-sign-machine:latest  -f docker/Dockerfile .
# 运行(cookies和账号密码两种方式二选一)
docker run \
  --name auto-sign-machine \
  -d \
  --label traefik.enable=false \
  -e enable_unicom=true \
  -e user=131*******12 \
  -e password=11****11 \
  -e appid=f7af****ebb \
  auto-sign-machine:latest
```

### 注意
#### cron中`%`号需要转义`\%`

### 脚本运行机制
任务并非在一次命令执行时全部执行完毕，任务创建时会根据某个时间段，将所有任务分配到该时间段内的随机的某个时间点，然后使用定时任务定时运行脚本入口，内部子任务的运行时机依赖于任务配置项的运行时间及延迟时间，这种机制意味着，只有当脚本的运行时间在当前定时任务运行时间之前，脚本子任务才有可能有选择的被调度出来运行

### crontab 任务示例
在4-23小时之间每隔三十分钟尝试运行可运行的脚本子任务
```txt
*/30 4-23 * * * /bin/node /workspace/AutoSignMachine/index.js unicom --user 1******5 --password 7****** --appid 1************9
```

### 多用户配置
启用`--accountSn`表示账户序号，例如`1,2`, 则将提取`option-sn`选项的值，例如`user-1`,`user-2`

### 配置文件示例
启用`--config /path/to/mycfg.json`表示配置文件
```json
{
    "accountSn": "1,2",
    "user-1": "22******1",
    "password-1": "31******1",
    "appid-1": "41******1",
    "user-2": "25******1",
    "password-3": "72******1",
    "appid-2": "92******1"
}
```

### 运行测试
```sh
## 立即模式, 一次性执行所有任务，仅建议测试任务是否正常时运行，该方式无法重试周期任务
## 该模式不缓存cookie信息，频繁使用将可能导致账号安全警告
#增加 --tryrun

## 指定任务模式，可以指定仅需要运行的子任务，多用户使用规则参看`多用户配置`
#增加 --tasks taskName1,taskName2,taskName3
```

