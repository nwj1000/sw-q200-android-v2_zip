# SW-Q200 蓝牙控制器 - Android 项目 v2

完整可编译的 Android 原生 BLE 应用，版本严格匹配，开箱即用。

## 版本配置（已严格对齐，不会再报 HasConvention 错误）

| 组件 | 版本 |
|------|------|
| Android Gradle Plugin | 7.4.2 |
| Gradle | 7.5 |
| Kotlin | 1.8.0 |
| compileSdk | 33 |
| minSdk | 24 (Android 7.0+) |
| targetSdk | 33 |

## 项目结构

```
sw-q200-android-v2/
├── settings.gradle
├── build.gradle
├── gradle.properties
├── gradle/
│   └── wrapper/
│       └── gradle-wrapper.properties
├── .github/
│   └── workflows/
│       └── build-apk.yml    # GitHub Actions 自动编译
└── app/
    ├── build.gradle
    └── src/main/
        ├── AndroidManifest.xml
        ├── java/com/swq200/controller/
        │   └── MainActivity.kt
        └── res/
            ├── layout/activity_main.xml
            └── values/
                ├── strings.xml
                ├── colors.xml
                └── themes.xml
```

## 两种编译方式

### 方式一：GitHub 在线编译（推荐，不用装任何开发工具）

1. 注册 GitHub 账号，新建仓库 `sw-q200-ble-app`
2. 把本项目所有文件上传到仓库根目录（不要传 `.gradle`、`build` 文件夹）
3. 打开 **Actions** 标签，会自动触发编译
4. 等待 3~5 分钟，绿色对勾即成功
5. 点进任务 → 底部 Artifacts → 下载 `sw-q200-controller-apk`
6. 解压得到 APK，传到华为手机安装

> 注意：必须是 **Public** 公开仓库（免费版可用Actions）

### 方式二：本地 Android Studio 编译

1. 安装 Android Studio Arctic Fox (2020.3.1) 或更高版本
2. **项目路径必须是纯英文**，不能有中文/空格/特殊字符
   - 正确示例：`E:\dev\sw-q200-android-v2`
   - 错误示例：`E:\项目\二次开发\...`
3. 打开 Android Studio → Open → 选择项目根目录
4. 等待 Gradle 自动同步（首次需下载依赖）
5. Build → Build APK(s) → 生成的 APK 在 `app/build/outputs/apk/debug/`

## 功能列表

- ✅ BLE 自动扫描，自动识别 SW-Q200
- ✅ 远程模拟 10 个实体按键（ATK001# ~ ATK00A#）
- ✅ 距离大字号实时显示
- ✅ 双轴角度 X/Y 显示
- ✅ 系统信息/当前记录/屏幕数据查询
- ✅ Hex 通信日志
- ✅ 分包重组处理

## 使用方法

1. 打开 SW-Q200 测距仪，开启蓝牙
2. 手机打开 APP，授予蓝牙+定位权限
3. 点「连接蓝牙设备」，自动连接
4. 点 READ 远程触发测距，数据自动回显

## 常见问题

**Q: 同步报错 `HasConvention`？**
A: 检查 Gradle 版本是不是 7.5，AGP 版本是不是 7.4.2。这两个必须严格匹配。

**Q: 路径报错？**
A: 把项目移到纯英文路径下，比如 `E:\dev\` 开头。

**Q: 搜不到设备？**
A: 确认测距仪蓝牙已开、手机定位已开、距离在 5 米内。

**Q: 能蓝牙控制拍照吗？**
A: 不能。协议未开放拍照指令，拍照需手动按机器按键。
