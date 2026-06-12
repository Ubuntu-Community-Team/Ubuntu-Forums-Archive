---
title: "Boot Problems"
date: 2019-09-12
forum: General Help
---

### Post by oluwafenyi on 2019-09-12
Hey. Please Help! I'm currently having boot problems.  I'm new to ubuntu so forgive the terrible terminologies  used.
Booting normally takes me to the Ubuntu screen with the dots and I remain there indefinitely. I tend to get better luck when booting into recovery mode and fiddling with Ctrl + Alt + any combination of F1-F4. That's the only way I can boot successfully to my desktop.
I recently installed boot-repair on one of my successful booting operations and this was generated: [http://paste.ubuntu.com/p/TxWPcBjnYQ/](http://paste.ubuntu.com/p/TxWPcBjnYQ/).
Would love if someone can help me be able to boot consistently.

---

### Post by oldfred on 2019-09-12
I am not seeing anything in report that looks out of line.

What brand/model system?
What video card/chip?

Does Windows 7 boot ok?
You are mounting the Windows 7 partition and if it does not correctly mount that could be an issue.
If issues run chkdsk and defrag on your Windows 7 partitions, sda1 & sda2. You may need a Windows repair flash drive with repair console or installer with repair console.

You also are mounting using UUID, but mount point is also UUID. Often better to create a mount point with a more understandable description like /mnt/win7 or whatever you like and use that to mount.

Also some suggest different parameters for the mount:
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 
    
I also have seen this for parameters. noatime is recommended for SSD, relatime which it looks like yours defaulted to is ok for HDD. Forum is changing async which it should not do, no spaces allowed in parameters.
       > nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,fstype=ntfs,uid=1000,gid=1000,fmask=0002,dmask=0002

---

### Post by oluwafenyi on 2019-09-12
Hi, It's a Sony VAIO with Intel Integrated Graphics.
I can boot into Win7.
I'll take your advice and create a better mount point.

I've just noticed something different from the normal. I went to my settings to check the graphics after noticing choppy youtube videos. It's listed as llvmpipe - (LLVM 7.0, 128 bits)
I'm pretty sure it used to be intel. Could this be a contributing factor?

---

### Post by oluwafenyi on 2019-09-12
Seemed to be a graphics problem. Intel Ironlake Mobile now being used instead of llvm. I followed the first two steps of this: [https://askubuntu.com/questions/1062967/ubuntu-18-04-not-working-with-intel-integrated-graphics](https://askubuntu.com/questions/1062967/ubuntu-18-04-not-working-with-intel-integrated-graphics) and booting seems to be responsive.

---

