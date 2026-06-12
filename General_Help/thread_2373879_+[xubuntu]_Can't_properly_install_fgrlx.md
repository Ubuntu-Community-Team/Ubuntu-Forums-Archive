---
title: "+[xubuntu] Can't properly install fgrlx"
date: 2017-10-10
forum: General Help
---

### Post by khoriam on 2017-10-10
I have lots of problems with the drivers. Faced a problem - my laptop (Dell 5565) has hybrid graphic, Radeon A6-9200 + R5 M435 ([http://www.dell.com/nz/partner/p/inspiron-15-5565-laptop/pd](http://www.dell.com/nz/partner/p/inspiron-15-5565-laptop/pd)). Spent three days already while using different advices - couldn't solve the problem of not having the second card active. Tried the proprietary drivers FGRLX - didn't help. During steam launch there is an error "OpenGL GLX extension not supported by display". Before Xubuntu/Ubuntu tried linux mint, more information (but about mint case) is there - [https://forums.linuxmint.com/viewtopic.php?f=46&t=255154](https://forums.linuxmint.com/viewtopic.php?f=46&t=255154)

---

### Post by khoriam on 2017-10-10
Installed all over again - nothing. After installation from additional drivers, AMD control center says that "No AMD graphics driver is installer or the AMD driver is not functioning properly. Please install the AMD driver appropriate for your AMD hardware or configure using aticonfig". If I run aticonfig, it says "aticonfig: No supported adapters detected". The installation is clean, updated. Core is 3.13.xxx, xorg is 1.5.1.

---

### Post by QIII on 2017-10-10
Hello!

Which release of Ubuntu are you using?

---

### Post by khoriam on 2017-10-10
At the moment xubuntu 14.04.1 is installed. Tried all the same with:xubuntu 14.04.5, ubuntu 14.04.1/5,ubuntu 16.04 (it was horrible for me, frequent screen freezing, could move mouse only) and different linux mints.

---

### Post by QIII on 2017-10-10
Did you run

```
sudo amdconfig --initial --adapter=all 
```?

When you say vaguely that you tried all sorts of things, it's impossble for us to know exactly what you did and what the current state of your machine may be.  This makes diagnosis difficult to impossible.  It would be best to know exactly what you did.

As a side note, starting with 16.04 fglrx is no longer supported and will not work.

---

### Post by khoriam on 2017-10-10
> **QIII said:**
> Did you run

```
sudo amdconfig --initial --adapter=all 
```?

When you say vaguely that you tried all sorts of things, it's impossble for us to know exactly what you did and what the current state of your machine may be.  This makes diagnosis difficult to impossible.  It would be best to know exactly what you did.

As a side note, starting with 16.04 fglrx is no longer supported and will not work.

 **UPD:** amdconfig: No supported adapters detected

About all sort of things - I tried to install manually with deb packages, manually with the the linux_catalyst.run and so on. Right now I have a xubuntu timeshift point of restore of clean install (after full update) with all the soft preinstalled, will run the command you have offered. We can also start from beginning and in case I'll say whether I tried it or not.

---

### Post by QIII on 2017-10-10
It may be that the hardware itself is not supported by fglrx.

---

### Post by khoriam on 2017-10-10
How do I check it?

---

### Post by QIII on 2017-10-10
According the the release notes given [here]("http://support.amd.com/en-us/kb-articles/Pages/AMDCatalyst15-7LINReleaseNotes.aspx"), it does not appear that the R5 M400 series is supported by fglrx (Catalyst).

I would suggest getting your machine back to a clean state -- perhaps by reinstalling after backing up your important files.

Does 16.04 work if you do not try to install fglrx?

---

### Post by khoriam on 2017-10-10
I remember that my graphics adapter was recognized by some command as R5 M200 once. About reinstall - I don't think it's needed, I use timeshift for this (the way of trials and errors, huh). 16.04 doesn't work properly. It gives some strange screen before showing the Ubuntu logo - like on the pic [https://imgur.com/a/0s3vq](https://imgur.com/a/0s3vq) . Plus, 16.04 and other distros based on 16.04 do frequently freeze.

Also, xrandr --listproviders gives Providers: number : 0

---

### Post by QIII on 2017-10-10
The most likely reason it would have been "recognized" by 14.04 as an M200 family is that the M400 family was not introduced until 2016.

Again:  Is the behavior shown in your image before or after trying to install fglrx?

The M400 series are GCN (Graphics Core Next) technology, but are first generation.  AMD started with second generation GCN GPUs when they introduced AMDGPU.  They are working both backwards to first gen GCN and forward from second gen.

I did some research some time ago on which GPUs AMD lists as at least first gen GCN and [yours is among them]("https://theleftcoastgeek.net/index.php/categories/12-possible-amdgpu-pro-supported-gpus-by-the-end").  AMDGPU support for GCN GPUs starts with Ubuntu 16.04.

---

### Post by khoriam on 2017-10-10
> **QIII said:**
> The most likely reason it would have been "recognized" by 14.04 as an M200 family is that the M400 family was not introduced until 2016.

Again:  Is the behavior shown in your image before or after trying to install fglrx?

The M400 series are GCN (Graphics Core Next) technology, but are first generation.  AMD started with second generation GCN GPUs when they introduced AMDGPU.  They are working both backwards to first gen GCN and forward from second gen.

I did some research some time ago on which GPUs AMD lists as at least first gen GCN and [yours is among them]("https://theleftcoastgeek.net/index.php/categories/12-possible-amdgpu-pro-supported-gpus-by-the-end").  AMDGPU support for GCN GPUs starts with Ubuntu 16.04.

It was before the fgrlx. System didn't even let me to install fglrx Couldn't fine M435 mine (there is R7 M435) but well, it's a good news then. What should I do now, try to install 16.04?

---

### Post by khoriam on 2017-10-10
I've forgotten to ask - if there any difference between ubuntu and Xubuntu besides the DE?

---

### Post by QIII on 2017-10-10
Try 16.04 again, in case there was just some fluke in the install.

The Xubuntu team includes some different default apps as well as the xfce DE.

---

### Post by khoriam on 2017-10-10
Then gonna start right away with xubuntu 16.04, will report asap.

---

### Post by khoriam on 2017-10-10
Started from Live-USB. Problems faced from the very beginning. There were several black screens:
1st. Screen tearing like on the pic before (or similar), the message in the top-left corner. 
[0.015721] [Firmware Bug]: cpu 0. Invalid threshold interrupt offset 1 for bank 4 block 0 (MSR000000413=0xd00000000100000)
2nd. Without tearing
[ 9.328847] sd 2:0:0:0: [sdb] No Caching mode page found
[ 9.328855] sd 2:0:0:0: [sdb] Assuming drive cache: write through

---

### Post by QIII on 2017-10-10
Did you run a checksum on your download and check the integrity of the media after copying it?

I'm very surprised it's not working.

---

### Post by khoriam on 2017-10-10
Checksum was fine.

**UPD:** Grub integrity check said there was one error.

---

### Post by QIII on 2017-10-10
What was the error?

---

### Post by khoriam on 2017-10-11
Checked on different usb sticks, error persists. 
Error: /pool/main/s/shm-signed_1.32~16.04.1+0.9+14744791736c180c6 lubuntu_amd64.deb No such file or directory.
It was xubuntu 16.04.3 LTS, now downloading 16.04.2 and ubuntu 16.04.3

---

### Post by khoriam on 2017-10-11
Tried 16.04.2 xubuntu, there was no integrity error, but firmware bug and sdb mistakes were present. lspci showed vga as r5 m230 (which is better than 14.04 98e4 or smth like that), installing xubuntu now.

---

### Post by khoriam on 2017-10-11
I've managed to install AMDGPU-pro, went through various circles of hell (fully deleting boot partition included) but steam says... OpenGL GLX extension not supported by display.
glxinfo says:
name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfig

What do I do?

---

### Post by khoriam on 2017-10-12
Initial question was... Solved. Moved to another thread [>>>]("https://ubuntuforums.org/showthread.php?t=2374045") please close this one.

---

