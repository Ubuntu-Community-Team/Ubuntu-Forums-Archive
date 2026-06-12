---
title: "WebGL not working on chromium or firefox"
date: 2020-06-08
forum: General Help
---

### Post by robgtx1 on 2020-06-08
[COLOR=#242729][FONT=Arial][FONT=inherit][FONT=inherit][FONT=inherit]Im using Xubuntu 20.04 and I've been having trouble with firefox and chromium to use WebGL. In chromium it only works if I activate hardware acceleration but it works slow because of my integrated video card (Intel G33/31).[/FONT][/FONT][/FONT][/FONT][/COLOR][FONT=Arial][FONT=inherit]
[/FONT][/FONT]
[COLOR=#242729][FONT=Arial][FONT=inherit]I tried to test webgl on firefox and it doesn't work either.[/FONT]
[FONT=inherit]In windows 7 it works perfectly without problems, and previously I used linux mint and it also worked but now the problem appears when using xubuntu 20.04
[/FONT]
[FONT=inherit]Chromium gpu test: 
Graphics Feature Status Canvas: Software only. Hardware acceleration disabled Flash: Software only. Hardware acceleration disabled Flash Stage3D: Software only. Hardware acceleration disabled Flash Stage3D Baseline profile: Software only. Hardware acceleration disabled Compositing: Software only. Hardware acceleration disabled Multiple Raster Threads: Disabled Out-of-process Rasterization: Disabled OpenGL: Disabled Hardware Protected Video Decode: Disabled Rasterization: Software only. Hardware acceleration disabled Skia Renderer: Enabled Video Decode: Software only. Hardware acceleration disabled Viz Display Compositor: Enabled Vulkan: Disabled WebGL: Disabled WebGL2: Disabled
[/FONT]
[FONT=inherit]On firefox: WebGL 1 Driver Renderer WebGL creation failed: * tryNativeGL * Exhausted GL driver options.
[/FONT]
[FONT=inherit]Inxi details: inxi -SGx System: Host: zyrox-home Kernel: 5.4.0-33-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Xfce 4.14.2 Distro: Ubuntu 20.04 LTS (Focal Fossa) Graphics: Device-1: Intel 82G33/G31 Express Integrated Graphics vendor: Lenovo driver: i915 v: kernel bus ID: 00:02.0 Display: x11 server: X.Org 1.20.8 driver: intel unloaded: fbdev,modesetting,vesa resolution: 1280x1024~75Hz OpenGL: renderer: Mesa DRI Intel G33 v: 1.4 Mesa 20.0.4 direct render: Yes[/FONT]

[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2020-06-08
If it worked on Mint before probably driver problem. Try to update your driver with [https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa](https://launchpad.net/~kisak/+archive/ubuntu/kisak-mesa)

---

### Post by robgtx1 on 2020-06-08
It didn't work. I keep getting the same problem :-?

---

### Post by monkeybrain20122 on 2020-06-09
Could be a kernel issue, something like that happened to me before and upgrading kernel fixed it. Can you try boot into an older kernel and see what happens? Reboot, when it start booting hit esc, then choose advanced option, it should have 2 kernels, choose the one with lower number.

---

### Post by dragonfly41 on 2020-06-09
There has been some reports of WebView not working on some [Electron packages]("https://github.com/shd101wyy/markdown-preview-enhanced/issues/1380#issuecomment-631341305") .. and [discussed here]("https://www.electronjs.org/docs/api/webview-tag#enabling").
Could this be related since Electron is based on Chromium? Just a guess.

---

### Post by robgtx1 on 2020-06-09
> **monkeybrain20122 said:**
> Could be a kernel issue, something like that happened to me before and upgrading kernel fixed it. Can you try boot into an older kernel and see what happens? Reboot, when it start booting hit esc, then choose advanced option, it should have 2 kernels, choose the one with lower number.

Nope, tried with 5.4.0-26 and its still the same problem.

---

