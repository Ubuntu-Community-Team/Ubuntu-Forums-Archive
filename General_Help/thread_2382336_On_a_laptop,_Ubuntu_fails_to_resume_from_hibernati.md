---
title: "On a laptop, Ubuntu fails to resume from hibernation when using kernel 4.13.0-26"
date: 2018-01-11
forum: General Help
---

### Post by ronbu on 2018-01-11
On a laptop, Ubuntu 16.04 failed to resume from hibernation when using kernel 4.13.0-26 .   After entering the password to unlock the LUKS LVM, a message is indicating it is resuming from the swap volume.  Then the dots stop moving and the screen goes black and becomes stuck.  I have to turn off the computer to get it unstuck.  On a desktop computer with the same kernel, resuming from hibernation worked fine.  A workaround for those who have that problem with the 4.13.0-x kernel is to install the latest 4.4 kernel if the user is running Ubuntu 16.04 and purge any kernels that have a later version number.   That is what I did on the laptop and now hibernate works well.  This solution may not work if it's a newer laptop that has problems with the 4.4 kernel.

---

### Post by missmoondog on 2018-01-12
what worked for me was to switch to the x.org x server video drivers and remove the nvidia drivers. am still able to use the new 4.13 kernel now. always thought nvidia drivers were more of a pain than they're worth anyway. :(

---

### Post by ronbu on 2018-01-13
But, in my case; I do not use the nvidia drivers and I already several xserver xorg video drivers including AMDGPU, AMD/ATI, fbdev, intel, Nouveau, AMD/ATI Radeon and VESA.  Anyway, as long as the 4.4 kernel works well for me and as long as I use Xenial, I do not feel the need the switch to another newer major kernel version.

---

### Post by radax05 on 2018-01-16
Ubuntu 17.10.1 fails to resume / wakeup from hibernation when using kernel 4.13.0.25:
- tested with 2 (two) desktop PCs - (Aspire X3-710 & PC with Asus motherboard & Intel Core i5 5400)
- no additional graphic card, simply using the GPU that is integrated with the CPU
- one with a fresh Ubuntu MATE 17.10.1 and one with Ubuntu MATE 17.10 where all the updates have been installed (as far as I can see, the Intel microcode has been updated, too)
- **sudo pm-hibernate** will put the PC into hibernation
- restart will proceed normally until the files from the swap partition are decompressed, afterwards, the keyboard and the mouse are "dead" and the monitor switches into power saving mode
- you have to hard-stop (keep the power button pressed until the PC turns off) and restart the PC

The same issue when using the normal **Quit -> Hibernate** method (Hibernation was activated like described in this article: [https://help.ubuntu.com/lts/ubuntu-help/power-hibernate.html](https://help.ubuntu.com/lts/ubuntu-help/power-hibernate.html))

The issue with the wakeup from hibernation is not present when booting with kernel 4.13.0.21 (or older 4.13.0.x).

I've also tested with Linux Mint 18.2 and 18.3 (because Linux Mint is based on Ubuntu) using the latest kernel updates and in both cases wakeup from hibernation does not work (as described above).  If you boot with a previous kernel, everything is fine in Linux Mint, too.

---

### Post by jds102 on 2018-01-24
I see the same problem as radax05 on my Dell Inspiron 15 laptop (Intel Core i3-6006U). Kernel 4.13.0.21 hibernates and resumes without problems, but the two more recent kernels (4.13.0.25 and 4.13.0.31) fail: hibernate appears to succeed, but resume stops dead as radax05 describes. This happens whether I use the built-in hibernate capability or usw-susp, and whether my Gnome session uses xorg or Wayland.

/var/log/kern.log doesn't seem to help much. Its record of the failed attempt to resume is as follows:
Jan 23 21:10:13 bombay kernel: [   98.197921] Bluetooth: RFCOMM TTY layer initialized
Jan 23 21:10:13 bombay kernel: [   98.197937] Bluetooth: RFCOMM socket layer initialized
Jan 23 21:10:13 bombay kernel: [   98.197954] Bluetooth: RFCOMM ver 1.11
Jan 23 21:10:19 bombay kernel: [  104.454231] rfkill: input handler disabled
Jan 23 21:10:23 bombay kernel: [  108.416251] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jan 23 21:10:41 bombay kernel: [  126.528680] usbcore: deregistering interface driver uvcvideo
Jan 23 21:10:42 bombay kernel: [  126.919415] rfkill: input handler enabled
Jan 23 21:10:42 bombay kernel: [  127.240559] PM: Syncing filesystems ... 

This seems like a pretty definite bug.

---

### Post by bobsone on 2018-01-26
We have a Lenovo Ideapad, 8GB ram (11.5GB swap) and I5-7200.  It has dual boot Ubuntu Mate 16.04.3 (64 bit) and Windows 10. 

   
  [SIZE=2]The hibernate function was working correctly but (about two weeks ago) has developed the issue outlined in the preceding posts.  I.e. it hibernates successfully but the restart process proceeds through entering the password then the mouse (and track pad) and keyboard are unresponsive and the screen goes black.  I have to shut the computer down and restart it to get it running again.  [/SIZE]

  [SIZE=2]I have removed (and reinstalled and removed) the hibernate function/file I found here; [https://help.ubuntu.com/lts/ubuntu-h...hibernate.html]("https://help.ubuntu.com/lts/ubuntu-help/power-hibernate.html") and have tried [SIZE=3]***[FONT=&quot]sudo pm-hibernate[/FONT]***[/SIZE], which hibernates successfully but also fails to restart.[/SIZE]

   
  Any help appreciated, I would be nice to have the hibernate function back;
Regards.

---

### Post by jds102 on 2018-01-27
Today (Jan. 27 2018) a new kernel is released: 4.13.0.32. Unfortunately it shows no change in behaviour, i.e. the hibernate bug persists. Some response/action would be appreciated.

---

### Post by bobsone on 2018-01-28
> **jds102 said:**
> Today (Jan. 27 2018) a new kernel is released: 4.13.0.32. Unfortunately it shows no change in behaviour, i.e. the hibernate bug persists.
Same here, the issue hasn't changed.  Our kernal has updated from 4.13.0.31 to 4.13.0.32.

---

### Post by jds102 on 2018-02-09
I have filed a bug report on this. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1748373](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1748373).

---

### Post by jds102 on 2018-02-13
This bug is fixed in kernel 4.16.0. I don't know when that will be released as a regular Ubuntu upgrade, but presumably fairly soon.

---

### Post by jds102 on 2018-03-04
Further to my last posting, it appears that Ubuntu 18.04 (due out in just over a month from now) will ship with kernel 4.15, not 4.16. With this in mind, I have just tested kernel 4.15.7, which is currently the latest available upstream kernel. Good news: I was able to hibernate and resume without problems. So we should be free of this problem Real Soon Now.

---

### Post by spvkgn on 2018-05-15
Is there a way to get working hibernate in 18.04 LTS? After upgrade from 17.10 my PC fails to resume from hibernate now, so it's really annoying.

---

### Post by markackerman8@gmail.com on 2018-07-18
I was also having this problem plague me ... and a fix after many attempts was to re-install Ubuntu 18.04, and now it is working perfectly.  I am also using Nvidia's "tested" Driver, as Nvidia was the culprit before.

Perhaps it was the "sudo add-apt-repository ppa:graphics-drivers" ppa which installed "Extra" Stuff and/or the 396 driver which screwed up my laptop's hibernating ability.  Either way it works flawlessly at this time of writing with the NVidia's 390 tested driver.  Before switching to the Nouveau driver worked.

---

