---
title: "Mounting Problems in 16.04"
date: 2017-05-14
forum: General Help
---

### Post by ceil210 on 2017-05-14
I use Ubuntu 16.04; things were going swell for me until out of the blue my Windows partition became unmounted.  I keep Windows handy for gaming purposes but also do things on the drive while logged into Ubuntu.

```
ceil@eps:~$ sudo mount /dev/sda4 "/media/ceil/Ceil's Home/"Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

I restarted Windows, tried shutting it down and back on, even go far as hibernating, starting and doing a cold boot.  I would like to have this fixed! :P



Thanks for your time,
Alex

---

### Post by Bucky Ball on 2017-05-15
```
"/media/ceil/Ceil's Home/"Windows is hibernated, refused to mount.
```

Says it all and seems to be your current problem (which you caused by booting into Win and switching on hibernation). Boot into Windows and switch off hibernation. Windows needs to be shut down COMPLETELY or it will 'own' the drive. If Win is in hibernation, the machine doesn't actually shut down and no other OS will be able to access the drive.

Incidentally, it is never a good idea to be using the Windows OS partition from Ubuntu for regular day-to-day use. It shouldn't be used as a data partition as a Ubuntu data partition as well as a Win OS drive. One false move or you start accessing and altering Win OS files and your Win could be unbootable or worse.

Best to leave the Win OS partition alone while you are in Ubuntu and access only when required.

---

### Post by ajgreeny on 2017-05-15
You may have had a Windows update when you booted to that OS which has turned faststart (or is it fastboot?) on again meaning Windows always goes into its hibernation mode when you shutdown, bad news for dual booters.

Go into your BIOS or UEFI settings and make sure that faststart is definitely disabled.

---

### Post by Mark Phelps on 2017-05-15
Windows versions since Win8 have had a Windows setting known as Fast Startup --which is a new form of hibernation.  This keeps the Windows filesystems mounted even when Windows is not running -- thus preventing you from mounting and accessing them in Linux.

This is unrelated to Fast Boot -- which is a BIOS option, not Windows.

If you are running Windows 8 or newer, then read the details below about disabling Fast Startup:

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

### Post by ajgreeny on 2017-05-15
Thanks for putting me right abut Fast Startup Mark.

I have not used Windows since XP so it is all hearsay and what I've read elsewhere, when I try to help Windows users

---

### Post by ceil210 on 2017-05-15
Thanks for the help guys.  I limit my win useage in Ubuntu but DO watch myself.  It was fastboot that caught me off guard :). I used this command to get it working:

```
shutdown /s
```

This works totally.

---

### Post by Bucky Ball on 2017-05-15
Great news. As the problem's fixed, please mark as solved to help others using Thread Tools at the top right of this page.

Good luck. ;)

---

