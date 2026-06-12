---
title: "Chromium crashes on launch"
date: 2014-08-28
forum: General Help
---

### Post by M.A.L.M. on 2014-08-28
Hello kind folks,

Since yesterday night, whenever I launch Chromium it crashes and burns. I can't even turn off the extensions (none of which are new) or access the configuration settings... The whole thing just blows up spectacularly:

[ATTACH=CONFIG]255911[/ATTACH]

I don't think it's a profile corruption issue because it's also happening in my laptop. It must be some sort of incompatibility with other programs I have installed. I did update Google Chrome from 36 to 37 yesterday, and it's working fine with no sign of interference. I also updated LibreOffice to 3.4.1, but I doubt that has anything to do. Just to be sure I uninstalled both of those, but no joy. Has anyone seen this before? Can anyone enlighten me as to where I can find a log or something that could be useful?

BTW I'm running 14.04 64 bits

---

### Post by uRock on 2014-08-28
Start Chromium via the terminal , then share any errors it spits out.

---

### Post by M.A.L.M. on 2014-08-28
This is what I got:

```
me@myrig:~$ chromium-browser
[26301:26331:0828/195121:ERROR:raw_channel_posix.cc(139)] recvmsg: Connection reset by peer
[26301:26331:0828/195121:ERROR:channel.cc(297)] RawChannel fatal error (type 1)
[26301:26331:0828/195122:ERROR:raw_channel_posix.cc(139)] recvmsg: Connection reset by peer
[26301:26331:0828/195122:ERROR:channel.cc(297)] RawChannel fatal error (type 1)
```

---

### Post by M.A.L.M. on 2014-08-28
In my laptop I get different output:

```
my@mylap:~$ chromium-browser 
[4547:4547:0828/195553:ERROR:desktop_window_tree_host_x11.cc(1349)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[4547:4547:0828/195553:ERROR:command_buffer_proxy_impl.cc(152)] Could not send GpuCommandBufferMsg_Initialize.
[4547:4547:0828/195553:ERROR:webgraphicscontext3d_command_buffer_impl.cc(386)] CommandBufferProxy::Initialize failed.
[4547:4547:0828/195553:ERROR:webgraphicscontext3d_command_buffer_impl.cc(405)] Failed to initialize command buffer.
[4547:4582:0828/195553:ERROR:raw_channel_posix.cc(139)] recvmsg: Connection reset by peer
[4547:4582:0828/195553:ERROR:channel.cc(297)] RawChannel fatal error (type 1)
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[4547:4547:0828/195553:ERROR:command_buffer_proxy_impl.cc(152)] Could not send GpuCommandBufferMsg_Initialize.
[4547:4547:0828/195553:ERROR:webgraphicscontext3d_command_buffer_impl.cc(386)] CommandBufferProxy::Initialize failed.
[4547:4547:0828/195553:ERROR:webgraphicscontext3d_command_buffer_impl.cc(405)] Failed to initialize command buffer.
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[4547:4547:0828/195553:ERROR:command_buffer_proxy_impl.cc(152)] Could not send GpuCommandBufferMsg_Initialize.
[4547:4547:0828/195553:ERROR:webgraphicscontext3d_command_buffer_impl.cc(386)] CommandBufferProxy::Initialize failed.
[4547:4547:0828/195553:ERROR:webgraphicscontext3d_command_buffer_impl.cc(405)] Failed to initialize command buffer.

```

---

### Post by M.A.L.M. on 2014-08-28
I don't get it. Retried desktop and now I get this:

```
me@myrig:~$ chromium-browser 
[26454:26484:0828/195855:ERROR:raw_channel_posix.cc(139)] recvmsg: Connection reset by peer
[26454:26484:0828/195855:ERROR:channel.cc(297)] RawChannel fatal error (type 1)
[26454:26484:0828/195855:ERROR:raw_channel_posix.cc(139)] recvmsg: Connection reset by peer
[26454:26484:0828/195855:ERROR:channel.cc(297)] RawChannel fatal error (type 1)
[26454:26484:0828/195855:ERROR:raw_channel_posix.cc(139)] recvmsg: Connection reset by peer
[26454:26484:0828/195855:ERROR:channel.cc(297)] RawChannel fatal error (type 1)

```

---

### Post by ajgreeny on 2014-08-28
I get something very similar in terminal when I start chromium, but my version runs fine and does not crash.

I seldom use chromium as I still prefer Firefox, but occasionally a web-site will work in chromium and not in FF and sometimes the reverse, so both are needed.
```
~$ chromium-browser
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[30739:30739:0828/210513:ERROR:desktop_window_tree_host_x11.cc(1330)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)
[30739:30769:0828/210532:ERROR:raw_channel_posix.cc(139)] recvmsg: Connection reset by peer
[30739:30769:0828/210532:ERROR:channel.cc(297)] RawChannel fatal error (type 1)
[30739:30769:0828/210555:ERROR:raw_channel_posix.cc(139)] recvmsg: Connection reset by peer
[30739:30769:0828/210555:ERROR:channel.cc(297)] RawChannel fatal error (type 1)
```
PS:
I'm still using Xubuntu 12.04, not 14.04, so it is not something related to just trusty.

---

### Post by M.A.L.M. on 2014-08-28
Firefox is also my main browser, but I also use both Chrome and Chromium regularly, often at the same time! Apart from the obvious PepperFlash advantage of Chrome, this method helps me keep organised and allows me to have multiple accounts open at the same time.

> I get something very similar in terminal when I start chromium, but my version runs fine and does not crash.

Anyway, I still don't know what's wrong, probably because I have no idea what those error messages mean. It is certainly puzzling that you have similar errors but it still runs.

---

### Post by M.A.L.M. on 2014-08-30
Just for fun, I have:
removed ~/.config/chromium
sudo apt-get purge chromium-browser
Rebooted and reinstalled a clean copy of Chromium... It still crashes.

---

