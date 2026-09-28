# Reality 域名筛选与检测指南

## 项目简介

本文介绍：

- Reality 节点搭建
- 目标域名筛选原则
- RealiTLScanner 扫描工具使用
- RealityChecker 检测工具使用

---

## 准备工作

### 环境要求

- VPS 一台（Ubuntu / Debian 等）
- RealiTLScanner
- RealityChecker

### 相关项目

| 项目 | 地址 |
|--------|--------|
| REALITY | https://github.com/XTLS/REALITY |
| RealiTLScanner | https://github.com/XTLS/RealiTLScanner |
| RealityChecker | https://github.com/V2RaySSR/RealityChecker |

---

## Reality 节点搭建

### 项目地址

https://github.com/XTLS/REALITY

---

## 目标域名筛选

### 域名要求

- 不使用跳转域名
- 支持 TLS 1.3
- 支持 X25519
- 支持 HTTP/2
- SNI 与域名一致
- 尽量避免 CDN

---

## 使用 RealiTLScanner 扫描

### 下载

#### Windows

https://github.com/XTLS/RealiTLScanner/releases

#### macOS

https://github.com/LiZu-KJ/RealiTLScanner/releases

---

### Linux/macOS

进入桌面：

```bash
cd Desktop
```

开始扫描：

```bash
./RealiTLScanner \
  -addr VPS_IP \
  -port 443 \
  -thread 100 \
  -timeout 5 \
  -out file.csv
```

### Windows

```powershell
cd "%USERPROFILE%\Desktop"
```

```powershell
RealiTLScanner-windows-64.exe ^
  -addr VPS_IP ^
  -port 443 ^
  -thread 100 ^
  -timeout 5 ^
  -out file.csv
```

---

## RealityChecker 使用方法

### 下载

#### Linux AMD64

```bash
wget https://github.com/V2RaySSR/RealityChecker/releases/latest/download/reality-checker-linux-amd64.zip
```

#### Linux ARM64

```bash
wget https://github.com/V2RaySSR/RealityChecker/releases/latest/download/reality-checker-linux-arm64.zip
```

---

### 安装

安装 unzip：

```bash
apt update && apt install -y unzip
```

解压：

```bash
unzip reality-checker-linux-amd64.zip
```

授权：

```bash
chmod +x reality-checker
```

---

### 运行

```bash
./reality-checker
```

### 批量检测

```bash
./reality-checker csv file001.csv
```

---

## 附录

### S-UI 面板安装

```bash
bash <(curl -Ls https://raw.githubusercontent.com/alireza0/s-ui/master/install.sh)
```

### SSH 端口转发

```bash
ssh -L <本地端口>:127.0.0.1:<远程端口> <用户>@<服务器IP>
```

例如：

```bash
ssh -L 50000:127.0.0.1:50000 root@1.2.3.4
```

非默认 SSH 端口：

```bash
ssh -fN -p 2222 \
-L 50000:127.0.0.1:50000 \
root@1.2.3.4
```
