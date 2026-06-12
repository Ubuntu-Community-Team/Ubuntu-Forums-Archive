---
title: "Ubuntu +windows"
date: 2017-09-14
forum: General Help
---

### Post by stjannifer on 2017-09-14
can i use Ubuntu and windows both in same system???

---

### Post by Impavidus on 2017-09-14
Yes. You can dual boot, so you have both systems installed and can run one at a time, or you can install one or the other in a virtual machine.
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by wheatpenny2 on 2017-09-14
When you boot from the Ubuntu DVD, and select "Install Ubuntu", the installer will say that Windows is already on the computer and it will offer you some choices, one of which is "Install Ubuntu alongside Windows". When you pick that, then another screen will allow you to decide how much hard drive space goes to each OS.
And when you get it installed, then go into BIOS and change the boot order to put Ubuntu on top then every time you boot (or reboot) you'll get a screen asking you which OS you want to use. (if you don't put Ubuntu at the top of the boot order then the computer will boot into Windows every time and not give you the choice to use Ubuntu).

---

### Post by mörgæs on 2017-09-15
If you want a dual boot the best approach is to shrink Windows using Windows itself, not from an Ubuntu boot.

---

### Post by Lloydb39 on 2017-09-16
Why? And how?

---

### Post by Lloydb39 on 2017-09-16
Morgaes: [h=2]+windows[/h][COLOR=#000000][INDENT]"If you want a dual boot the best approach is to shrink Windows using Windows itself, not from an Ubuntu boot."[/INDENT]
[/COLOR]
 Why? And how?

---

### Post by Impavidus on 2017-09-16
> **Lloydb39 said:**
> Morgaes: **+windows**

[COLOR=#000000][INDENT]"If you want a dual boot the best approach is to shrink Windows using Windows itself, not from an Ubuntu boot."[/INDENT]
[/COLOR]
 Why? And how?

The file system used on Windows, NTFS, has some peculiarities that are not so well documented, which means that developers of Linux tools to modify NTFS partitions have to guess some things, making those tools less reliable. The build-in tools of Windows are reliable when dealing with those partitions. Similarly, when modifying Linux partitions, use Linux tools, as Microsoft didn't bother building support for Linux partitions into Windows. Which makes sense, somewhat. Use the partitioning tool that's build-in to Windows.

Note that dual booting Ubuntu and Linux is no longer as easy as it used to be ten years ago. Windows doesn't always simply ignore Linux and UEFI firmware isn't always comforming to standards and making things harder. That's why virtual machines are suggested too. I don't use virtual machines myself. I take care of two computers, one dual booting two Ubuntu versions, one dual booting Ubuntu and WinXP (the latter always off-line), which was more coöperative than Win8 or Win10.

---

### Post by dragonfly41 on 2017-09-16
I am currently using Ubuntu 16.04 from an external USB container interfaced to an old laptop which has a dual boot installation.
The internal Ubuntu OS comes in handy when I have to troubleshoot the external Ubuntu OS (quite often since my laptop is now due for replacement).
The point I'm making is that you have the option to keep Ubuntu quite separate in a disk drive inside a USB container.
Of course you need to purchase a disk and USB container but these are needed anyway for backup purposes.

I will be purchasing a new tower PC with Window 10 and I will be able to just plugin my Ubuntu container. 
I will configure BIOS to boot up external OS.

---

