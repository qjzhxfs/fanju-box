# 番剧盒 fanju-box

安卓端番剧播放器：直接读 **WebDAV 网盘**或**手机本地文件**看番，不需要 Emby / Jellyfin 服务器。
包名 `app.fanju.box`，Kotlin + Jetpack Compose + Media3(ExoPlayer)。

## 功能

- **媒体源**：WebDAV（Alist/OpenList、群晖、Nextcloud、坚果云，Basic Auth）+ 本地文件夹（SAF，不需要存储权限）
- **库扫描**：递归识别视频，按文件夹聚合成番剧；集数解析 `01` / `第1集` / `S01E01` / `EP05`，自然排序，自动跳过 QQ/Telegram/Download 等目录
- **刮削**：Bangumi 公开 API 取中文名、简介、封面、评分、年份，可手动搜索纠正；刮不到时用视频帧当封面
- **海报墙 / 详情页 / 选集 / 继续观看**
- **播放**：Media3，WebDAV 直链带鉴权头、`content://` 本地文件、断点续播、上一集/下一集
- **字幕**：同目录 srt/ass/ssa/vtt 自动匹配（支持整目录共用一条字幕），内嵌字幕轨道
- **弹幕**：同目录 bilibili XML / 弹弹play JSON 自动加载；设置里填弹弹play AppId/AppSecret 后可按番剧名拉取网络弹幕；自绘弹幕层，滚动/顶部/底部按轨道排布
- **手势**：左右滑快进（带时间预览）、左半屏上下滑亮度、右半屏上下屏音量、长按 3x、双击暂停、单击显隐控制栏

## 弹弹play 接入

只调用官方开放弹幕网络 `https://api.dandanplay.net` 的公开接口（搜索、弹幕、番剧信息），请求头 `X-AppId` / `X-AppSecret`。
不自建镜像、不缓存分发弹幕库、不做任何二次分发；弹幕仅在本机播放器里渲染。

## 由来

需求来自 Tigerest Theater（Qt + Emby 客户端）。那套界面与数据层绑在 Emby API 上，这里按它「海报墙 + 刮削 + 播放器」的思路用原生 Android 重写，并去掉服务器依赖。

## 状态

自用开发中，未上架应用商店；已在 Alist（WebDAV）+ 手机本地库上实测通过扫描、刮削、串流播放、字幕与本地弹幕。
