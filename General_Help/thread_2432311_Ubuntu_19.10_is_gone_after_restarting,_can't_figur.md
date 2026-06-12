---
title: "Ubuntu 19.10 is gone after restarting, can't figure out how to find it again"
date: 2019-11-30
forum: General Help
---

### Post by futurehusband93 on 2019-11-30
Ubuntu 19.10 is no longer available to boot from my PC. I installed it a few days ago dual boot with Windows 7, because I'm learning programming. Today when I turned my PC on, it skipped grub and booted straight to Windows, so I turned it off again, went to boot menu manually, and it's not there anymore, only my normal hard drives.

There may have been an update when I shut down before the problem, but apparently Windows 7 should only have security updates now, so I don't know if it still affected it.

The partition is still technically there, but when I tried to reinstall it, it tells me it's already installed, but I can't physically boot it.

I've tried downloading Super Grub2 Disk and booting from it, but it just came back with this.


Welcome to GRUB!

error: unknown filesystem.
error: unknown filesystem.
error: unknown filesystem.
error: unknown filesystem.
error: unknown filesystem.
error: unknown filesystem.
error: unknown filesystem.
error: unknown filesystem.
error: unknown filesystem.
Entering rescue mode...
grub rescue>



When I try to reinstall, I get the message to install alongside Ubuntu 19.10, which is the one that's already on there, and when I check the advanced installation the partition is still there too.

I'm trying to learn programming, but this is seriously holding me back. As I've not done much yet, I don't really have any qualms around simply reinstalling over the current partition and losing all the old data, but the problem is I don't know what happened, and I don't know how to stop it from happening again.

---

### Post by Impavidus on 2019-11-30
Most likely some Windows update overwrote the bootloader and the Windows bootloader can't boot Linux.

Use a live disk to run Ubuntu on your computer, then install and use [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I expect the default repair will fix this (it will reinstall grub), but to be really sure, you can first create a boot info summary and show us the link.

---

### Post by futurehusband93 on 2019-12-01
I put boot repair onto a USB and booted it. Ran it on the regular repair mode, and this is what came up

[https://ibb.co/kJwyFVp](https://ibb.co/kJwyFVp)

---

### Post by futurehusband93 on 2019-12-01
> **Impavidus said:**
> Most likely some Windows update overwrote the bootloader and the Windows bootloader can't boot Linux.

Use a live disk to run Ubuntu on your computer, then install and use [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). I expect the default repair will fix this (it will reinstall grub), but to be really sure, you can first create a boot info summary and show us the link.

Ran it again another way and it ended up like this

[https://ibb.co/Qfc9SPJ](https://ibb.co/Qfc9SPJ)

---

### Post by Impavidus on 2019-12-01
The bootloader is at least attempting to boot Ubuntu. But it fails.

Any chance of showing us a boot info summary? That may tell us a bit more than those error messages. Some information on your hardware may help as well.

---

### Post by futurehusband93 on 2019-12-01
> **Impavidus said:**
> The bootloader is at least attempting to boot Ubuntu. But it fails.

Any chance of showing us a boot info summary? That may tell us a bit more than those error messages. Some information on your hardware may help as well.


```
ubuntu@ubuntu:~$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
 Simple tool to repair frequent boot problems.

Website: https://sourceforge.net/p/boot-repair/home
 More info: https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Hit:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Get:3 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu eoan InRelease [15.4 kB]
Get:4 http://archive.ubuntu.com/ubuntu eoan InRelease [255 kB]                
Get:6 http://security.ubuntu.com/ubuntu eoan-security InRelease [97.5 kB]      
Get:7 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu eoan/main amd64 Packages [1704 B]
Get:8 http://archive.ubuntu.com/ubuntu eoan-updates InRelease [97.5 kB]
Get:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu eoan/main Translation-en [1576 B]
Get:10 http://security.ubuntu.com/ubuntu eoan-security/main amd64 Packages [87.4 kB]
Get:11 http://security.ubuntu.com/ubuntu eoan-security/main Translation-en [32.5 kB]
Get:12 http://security.ubuntu.com/ubuntu eoan-security/main amd64 DEP-11 Metadata [200 B]
Get:13 http://security.ubuntu.com/ubuntu eoan-security/main DEP-11 48x48 Icons [29 B]
Get:14 http://security.ubuntu.com/ubuntu eoan-security/main DEP-11 64x64 Icons [29 B]
Get:15 http://security.ubuntu.com/ubuntu eoan-security/main amd64 c-n-f Metadata [1940 B]
Get:16 http://security.ubuntu.com/ubuntu eoan-security/restricted amd64 Packages [5140 B]
Get:17 http://security.ubuntu.com/ubuntu eoan-security/restricted Translation-en [1188 B]
Get:18 http://archive.ubuntu.com/ubuntu eoan/main amd64 Packages [969 kB]
Get:19 http://archive.ubuntu.com/ubuntu eoan/main amd64 DEP-11 Metadata [510 kB]
Get:20 http://archive.ubuntu.com/ubuntu eoan/main DEP-11 48x48 Icons [95.4 kB]
Get:21 http://archive.ubuntu.com/ubuntu eoan/main DEP-11 64x64 Icons [173 kB]
Get:22 http://archive.ubuntu.com/ubuntu eoan/main amd64 c-n-f Metadata [29.7 kB]
Get:23 http://archive.ubuntu.com/ubuntu eoan-updates/main amd64 Packages [127 kB]
Get:24 http://archive.ubuntu.com/ubuntu eoan-updates/main Translation-en [47.6 kB]
Get:25 http://archive.ubuntu.com/ubuntu eoan-updates/main amd64 DEP-11 Metadata [25.6 kB]
Get:26 http://archive.ubuntu.com/ubuntu eoan-updates/main DEP-11 48x48 Icons [7781 B]
Get:27 http://archive.ubuntu.com/ubuntu eoan-updates/main DEP-11 64x64 Icons [11.4 kB]
Get:28 http://archive.ubuntu.com/ubuntu eoan-updates/main amd64 c-n-f Metadata [2932 B]
Get:29 http://archive.ubuntu.com/ubuntu eoan-updates/restricted amd64 Packages [5140 B]
Get:30 http://archive.ubuntu.com/ubuntu eoan-updates/restricted Translation-en [1188 B]
Fetched 2603 kB in 1s (3575 kB/s)                
Reading package lists... Done
Ign:1 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan InRelease
Hit:2 cdrom://Ubuntu 19.10 _Eoan Ermine_ - Release amd64 (20191017) eoan Release
Hit:3 http://archive.ubuntu.com/ubuntu eoan InRelease
Hit:4 http://security.ubuntu.com/ubuntu eoan-security InRelease     
Hit:5 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu eoan InRelease
Hit:6 http://archive.ubuntu.com/ubuntu eoan-updates InRelease
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install -y boot-info && boot-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 boot-info : Depends: boot-sav but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
ubuntu@ubuntu:~$ 

```

My hardware is as follows

Intel Core i5-6600K 3.5GHz CPU
Nvidia GTX 980 Ti 4gb
Gigabyte Z170-Gaming 3 Motherboard
16gb Ram

---

