---
title: "linux server (-ish) on i.MX6q board"
date: 2022-01-29
forum: General Help
---

### Post by boschetto on 2022-01-29
hi! first of all, im new, both to the forum and to the linux world, so dont take anything for granted with me.

as the geek that i am, i somehow went from having a cold and watching some shows to wanting a little ftp/dlna local server in the span of 3 days. after some digging in the scrap bin i found a i.MX6quadro SABRE lite board suitable for my needs (aka it has a sata port). this wonderful thing has a arm quad core, 1GB of ram and a gigabit ethernet port and even more important its free. after almost a month of toying with it, last week i somehow managed to run a pre-packaged image of ubuntu 18 on it, and after some hours of trying stuff im still stuck and im unable to launch a graphic enviroment. i know, its a bit of an eresy, but as a beginner i need some visual help while doing stuff.

[https://boundarydevices.com/ubuntu-bionic-18-04-3-lts-for-i-mx6-7-boards-with-etnaviv-gpu-acceleration-january-2020-mainline-kernel-5-4-6/](https://boundarydevices.com/ubuntu-bionic-18-04-3-lts-for-i-mx6-7-boards-with-etnaviv-gpu-acceleration-january-2020-mainline-kernel-5-4-6/) on this page there is the image that im running and some supported stuff. 

right now im trying to launch xfce, wich is already installed but its trying to stream the graphical interface using X11 i think (?). as i said im new to this, im attaching a few images so someone can figure out something more than me. 

in this image there is just the login screen, whitout doing anything it already tells me that the system is read only. why is doing that, and how can i change it? i assume i cant install a program with the read only filesystem.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289923&stc=1[/IMG]
here instead is the machine response to me trying to launch xfce. it talks about a X server,  but trying to connect from another pc using "ssh -X username@hostname" returns "xcb_connection_has_error() returned true", so again im not sure whats happening. 
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289922&stc=1[/IMG]

the image im running its exacly the same as the xfce one on the boundary page, i just added a file for the bootloader.

---

### Post by boschetto on 2022-01-30
so, after a bit of trial and error i remounted the main system disk as read and write and magically xfce started up by himself. now, the problem is that after each reboot the disk gets mounted as read only. i tried to modify fstab but even by changing "error=mount,ro" to "error=mount,rw" doesnt change anything.

---

