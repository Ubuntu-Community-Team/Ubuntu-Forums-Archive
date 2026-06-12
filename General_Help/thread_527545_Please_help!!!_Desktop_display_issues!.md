---
title: "Please help!!! Desktop display issues!"
date: 2007-08-16
forum: General Help
---

### Post by worty on 2007-08-16
Hi everyone

I have been having these display issues that are driving me insane. I'm not sure what is behind the problems but I think I have narrowed it down to an openGL issue since it seems to pop up when I use openGL either through XGL/compiz or mplayer with the openGL video output. I attached a picture of what I'm getting. I noticed that the problems started appearing when I updated a few packages (I think) having to do with openGL but I am not sure what packages they were anymore. Any help would be greatly appreciated!

---

### Post by dougfractal on 2007-08-16
lspci -nn

Have you handled your card. (static shock) or checked the cables?

---

### Post by worty on 2007-08-16
Thanks for the reply!! 

I am fairly certain that it's a software issue. My display acts normally until I use mplayer  or use xgl/compiz. Then, I get a bunch of yellow/cyan blue artifacts like those I showed. I also dual booted back into windows and it seems to be acting fine.


00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge [1106:3189]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8235 PCI Bridge [1106:b168]
00:0a.0 Ethernet controller [0200]: Macronix, Inc. [MXIC] MX987x5 [10d9:0531] (rev 20)
00:0e.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 05)
00:0e.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 05)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 50)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AP [Radeon 9600] [1002:4150]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary) [1002:4170]

---

### Post by dougfractal on 2007-08-16
is that driver "radeon" or driver "fglrx"
> 
grep  driver /etc/X11/xorg.conf

edit:
i've seen you are using xgl, so I guess its fglrx.

ati have a new driver (15th Aug). Envy will get it for you.

If that fails  try radeon 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

