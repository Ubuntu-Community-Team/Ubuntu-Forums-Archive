---
title: "LUBUNTU Disabled nvidia nouveau driver now the system not startup"
date: 2020-08-05
forum: General Help
---

### Post by aug7744 on 2020-08-05
Here Lubuntu 20.04 and using nouveau nvidia.
Is how if that driver not is fast or not using exactly the video card speed.
Thus I had downloaded the latest nvidia proprietary driver, but had to disable nouveau driver.
I had done the follow commands

$ sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
$ sudo update-initramfs -u
$ sudo reboot

Now Lubuntu start and freeze in Lubuntu logo and not continue starting.
I have full write read access in Lubuntu system partition using windows.
How to fix it ?
Linux had to be more simple and have two modes one to users that wait have access to system and other mode to install driver how windows does.
How is hard to install video card driver in Linux.

---

### Post by TheFu on 2020-08-05
> How is hard to install video card driver in Linux. 
It depends on the specific card.  Well supported cards install the correct drivers automatically in 20.04.
Don't touch Linux partitions from Windows.  Use a Try Ubuntu boot flash/DVD/CDROM instead.  That is the standard way to fix issues.

You should not blacklist nouveau until after the other driver you want is installed. I've never had as much trouble as you seem to be having, but I don't have any 20.04 systems running on physical hardware. Too new for me.

---

### Post by ActionParsnip on 2020-08-05
Use root recovery (Hold SHIFT at boot and select root). You can then run
```

mount -o remount,rw /
mv  /etc/modprobe.d/blacklist-nvidia-nouveau.conf  /etc/modprobe.d/blacklist-nvidia-nouveau.conf-old
exit

```
Then resume boot. Say YES to the next prompt and you have rolled back your change

---

### Post by CelticWarrior on 2020-08-05
> **TheFu said:**
> You should not blacklist nouveau until after the other driver you want is installed. I've never had as much trouble as you seem to be having, but I don't have any 20.04 systems running on physical hardware. Too new for me.

Indeed. And I never had to blacklist nouveau as this is typically done by the installation of the proprietary Nvidia drivers. I really don't know why some people complicate things so much.

---

### Post by TheFu on 2020-08-05
> **CelticWarrior said:**
> Indeed. And I never had to blacklist nouveau as this is typically done by the installation of the proprietary Nvidia drivers. I really don't know why some people complicate things so much.

He tried the "easy way" and it didn't work as expected (that happens to all of us from time to time), so 30 minutes of google found some commands. All very reasonable, especially when some things are broken.  After all, the 20.04 release notes specify issues with nvidia GPUs.  People new are unlikely to read those notes and likely to get caught with the problems listed inside for nvidia, samba, and a few others.  

The release notes for 20.04.1 say 
>  1881586 Add support for the new -server NVIDIA drivers . 
[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes/ChangeSummary/20.04.1](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes/ChangeSummary/20.04.1)  Appears there are hundreds of fixes.  Hopefully, the OP did a sudo apt full-upgrade to move from 20.04 ---> 20.04.1 already.

---

### Post by aug7744 on 2020-08-06
I want try to install nvidia proprietary driver and had information about nouveau driver and nouveau kernel driver.
I not had knowledge if nouveau driver and nouveau kernel driver are or not the same component.
Thus I had created an post in
[https://ubuntuforums.org/showthread.php?t=2448255](https://ubuntuforums.org/showthread.php?t=2448255)
with title  "LUBUNTU How to disable nouveau kernel driver to install proprietary drivers ?"

Both naming are the same component ?

---

### Post by TheFu on 2020-08-06
Yes. Video drivers are all kernel modules. To see if nvidia drivers are loaded into the kernel, something like this:
```
$ lsmod |grep nvid
```
For Intel, 
```
$ lsmod |grep i9
```
Or just use 
```
$ lspci -vk |perl -lne 'print if /VGA|3d/i .. /^[\w]*$/'
```

There are a few other ways to see which is being used.  

No kernel driver of any sort can be changed on a system actively using them. For people new to Linux, the easiest solution for video drivers is to reboot, but it is possible to use a different tty/console, kill all X11 or Wayland processes, then swap the drivers and restart the X11 display host, switch to the graphical TTY (used to be <cntl>-<alt>-F7) - different consoles are available under <c>-<a>-F1 thru F8.  For now, probably just reboot.

When seeking solutions via google, for now, always specify the release being used "ubuntu 20.04.1" along with the question.  Many of the questions posted have release-dependent answers.  

Before 18.04, loading nvidia drivers was different than it is today. Also, due to the license requirements from nvidia, their drivers are handled differently from Intel and AMD drivers.  There's a famous photo of Linus Torvalds showing what he thinks about nvidia's Linux support. [https://www.wired.com/2012/06/nvidia-linus-torvald/](https://www.wired.com/2012/06/nvidia-linus-torvald/)  I have nvidia GT 430 and GT 1030 on 2 boxes here.  I've been burned with both Intel and AMD GPU support in the past, though by far, Intel has been the least problematic GPUs and meet all my needs, except the whole wrong CPU problem.  I've also been disappointed by nvidia ending driver support for some older cards and nouveau drivers not supporting the desired resolution for that card.

---

### Post by aug7744 on 2020-08-13
Reinstalled the system.
The problem was because I want to use latest Nvidia proprietary metapackage version 450 and only was displayed to select previous versions. Thus I had try an solution, but not had knowledge about add graphics PPA and will be displayed the latest nvidia driver.
Now working correctly.
Thanks very much :)

---

