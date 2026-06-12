---
title: "only 4 characters are visble per line the rest of the characters are invisible"
date: 2021-04-11
forum: General Help
---

### Post by rjhanson on 2021-04-11
Hello,
I Have 4 Ubuntu 20.10 computers, 2 ea desktops and 2 ea laptops.  After a recent update using the command line "upgrade", my text stopped working correctly on only one computer.  On all my programs and the terminal, the 1st 4 characters are displayed in black, after that the text is the same color as the background. I opened libreoffice writer and typed text into and had the same problem, 1st 4 characters are black and the rest are the background color.  I selected the text that were the same color as the background color and chose a different color, but it would not change them. The terminal has the same issue.

All the other Ubuntu 20.10 systems work normal with the same updates.

Any clue as to what I did to mess my text up?

Thanks
Richard

---

### Post by timothy-red-groves on 2021-04-11
This also happened to me.  I'd just logged in to post this very subject myself.  I wanted to include a screenshot, but apparently I'm not allowed to.  I note that Firefox and Thunderbird are not affected by this problem, but everything else seems to be.  I am running XUbuntu 20.04, and the problem started after my last update, which included Vulkan.
EDIT:  Calibre, XLinks and Steam are not affected, nor any application running under Wine.  Most QT-based apps seem to be unaffected.  Is this perhaps related to GTK?

---

### Post by Impavidus on 2021-04-12
May be related to this issue: [https://ubuntuforums.org/showthread.php?t=2460057](https://ubuntuforums.org/showthread.php?t=2460057)
No replies on that thread, which suggests that nobody had a clue. I can't find a relevant bug report.

Given the rarity of questions about this issue, despite the very obvious symptoms, and the fact that it's related to font rendering, I suspect it may have something to do with graphics drivers. Some information on your graphics hardware may help. Get a list of all packages that were upgraded when this issue appeared. You can find them in /var/log/dpkg.log. Find out which programs are affected and which are not. Do the affected programs all depend (maybe indirectly) on one of the upgraded packages and the unaffected programs not?

Consider reporting a bug: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by timothy-red-groves on 2021-04-12
[FONT=monospace][COLOR=#000000]Distributor ID: Ubuntu[/COLOR]
Description:    Ubuntu 20.04.2 LTS
Release:        20.04
Codename:       focal
Linux Thor 5.4.0-70-generic #78-Ubuntu SMP Fri Mar 19 13:29:52 UTC 2021 x86_64 
x86_64 x86_64 GNU/Linux

Upgraded package list:
[/FONT]2021-04-11 08:23:51 upgrade libapt-pkg6.0:amd64 2.0.4 2.0.5
2021-04-11 08:23:52 upgrade apt:amd64 2.0.4 2.0.5
2021-04-11 08:23:54 upgrade apt-utils:amd64 2.0.4 2.0.5
2021-04-11 08:23:54 upgrade alsa-ucm-conf:all 1.2.2-1ubuntu0.5 1.2.2-1ubuntu0.6
2021-04-11 08:23:54 upgrade libdrm-common:all 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:54 upgrade libdrm2:i386 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:54 upgrade libdrm2:amd64 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:54 upgrade libdrm-amdgpu1:amd64 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:55 upgrade libdrm-amdgpu1:i386 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:55 upgrade libdrm-intel1:amd64 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:55 upgrade libdrm-intel1:i386 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:55 upgrade libdrm-nouveau2:i386 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:55 upgrade libdrm-nouveau2:amd64 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:55 upgrade libdrm-radeon1:amd64 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:55 upgrade libdrm-radeon1:i386 2.4.104+git2103311700.6d8216~oibaf~f 2.4.105+git2104091700.991e95~oibaf~f
2021-04-11 08:23:56 upgrade libegl-mesa0:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:23:56 upgrade libgbm1:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:23:56 upgrade libllvm12:amd64 1:12.0.0~++rc3-1~exp1~oibaf~f 1:12.0.0~++rc5-1~oibaf~f
2021-04-11 08:23:58 upgrade libllvm12:i386 1:12.0.0~++rc3-1~exp1~oibaf~f 1:12.0.0~++rc5-1~oibaf~f
2021-04-11 08:24:01 upgrade libgl1-mesa-dri:i386 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:02 upgrade libgl1-mesa-dri:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:03 upgrade libosmesa6:i386 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:04 upgrade libosmesa6:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:04 upgrade libglx-mesa0:i386 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:04 upgrade libglx-mesa0:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:05 upgrade libglapi-mesa:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:05 upgrade libglapi-mesa:i386 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:05 upgrade libgl1-mesa-dev:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:05 upgrade libgl1-mesa-glx:i386 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:05 upgrade libxatracker2:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:06 upgrade mesa-va-drivers:i386 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:06 upgrade mesa-va-drivers:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:07 upgrade mesa-vdpau-drivers:i386 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:07 upgrade mesa-vdpau-drivers:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:08 upgrade mesa-vulkan-drivers:i386 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:09 upgrade mesa-vulkan-drivers:amd64 21.1~git2103270600.b95c62~oibaf~f 21.1~git2104110600.ba8737~oibaf~f
2021-04-11 08:24:09 upgrade syncthing:amd64 1.14.0 1.15.1

---

### Post by timothy-red-groves on 2021-04-12
Attached is a screenshot of Geany, which is affected by this issue.

---

