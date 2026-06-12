---
title: "Unable to update windows 10 due to dual boot with 18.04 LTS?"
date: 2018-06-14
forum: General Help
---

### Post by shstan on 2018-06-14
I am currently dual booting my 18.04LTS along with windows 10.  
Unfortunately, I cannot somehow update my windows right now, possibly due to the fact that having ubuntu partition conflict something with it.  
I have been kept getting errors on the windows side that the update could not be installed and keeps undoing changes everytime I reboot.  
Is this happening because I did not create a separate swap partition for Ubuntu? This only started happening very recently, and I have successfully updated windows alongside with Ubuntu before.  
The error code is with .NET apparently (0x800f0922), but I double checked that .NET is activated in the windows features. That made me wonder if it is the ubuntu partition that is messing with windows update...

---

### Post by yancek on 2018-06-14
Ubuntu does not use a swap partition any longer but a swap file so that's not the problem.  Your Ubuntu and windows systems are totally separated and are on different partitions so having Ubuntu or another OS on the computer isn't going to affect it.  I would suggest you do an online search for your error and I am sure that will be more productive.  YOu should find a number of sites like the one below which gives some causes and solutions for the windows update problem.   It appears to be a pretty common problem with windows and has been around for quite some time.

[https://www.easeus.com/backup-utility/windows-10-update-with-error-code-0x800f0922-issue.html](https://www.easeus.com/backup-utility/windows-10-update-with-error-code-0x800f0922-issue.html)

---

### Post by leunam12 on 2018-06-15
The first thing that I would do is run the Windows update troubleshooter. Many times that solves the issue.

[https://support.microsoft.com/en-us/help/4027322/windows-update-troubleshooter](https://support.microsoft.com/en-us/help/4027322/windows-update-troubleshooter)

---

### Post by travis-falkenberg on 2018-06-16
If your boot disk is MBR then I would install a standard DOS MBR to boot Windows only. Then see if Windows updates successfully.

I had to do this last year while running Windows7. It refused to update and kept undoing changes. Sorry I can't remember which Windows updates caused the problem.

You can make a bootable usb and use boot-repair to install a standard DOS MBR. Use boot repair to reinstall grub to get back to your Ubuntu installation.

  [https://sourceforge.net/projects/boot-repair-cd/files/](https://sourceforge.net/projects/boot-repair-cd/files/)

---

