---
title: "Wubi/Ubuntu &amp; Hal"
date: 2007-06-30
forum: General Help
---

### Post by spnoe on 2007-06-30
I recently updated in the normal method and the update was HAL. The update went well but when I restarted Ubuntu I received a message saying HAL failed.

I expect others are experiencing the same problem as I have installed twice and all works well until I intastall the update to HAL.

My question is should we use the update with WUBI and is there a way around trhis error without having to re-install and not installing the update?

Thanks for help.

Steve

---

### Post by BlueFiberOptics on 2007-07-01
I had this exact problem and I just uninstalled Wubi and figured it was something with Ubuntu.  So is it really Wubi that is the cause of the HAL not working after updates?

---

### Post by ago on 2007-07-02
I cannot reproduce that. I updated a new installation and everything worked fine. Can anybody else confirm this?

---

### Post by ago on 2007-07-02
You may want to run chkdisk from windows and see if that fixes the issue.

---

### Post by Spegelius on 2007-07-12
Actually, i'm having the exact same problem; booted my server Wubi-installation (the one that i completted when testing the RAID support inclusion) and update lupin and then allowed all the other updates to install. After booting, the HAL-problem crept up and it's been on ever since. Even tried re-installing all installed hal* packages manually, but no joy. The HAL process startup seems to stop with error code 1 (that's as much i can seem from the boot output and syslog doesn't even show that...).

I'll try booting with the earlier kernel, not the latest.

---

### Post by ago on 2007-07-12
Spegelius try to see if you can get some more info, I cannot reproduce that

---

### Post by murkin on 2007-07-15
i just ran across the same issue. the solution for me was found here:

[http://ubuntuforums.org/showthread.php?t=456395](http://ubuntuforums.org/showthread.php?t=456395)

"/var/cache/hald/fdi-cache" was somehow renamed into "/var/cache/hald/fdi-cache~"

After I renamed this file and rebooted, all seems back to normal. Looks like this is an issue with Ubuntu itself, not Wubi.

---

### Post by ago on 2007-07-15
> **murkin said:**
> Looks like this is an issue with Ubuntu itself, not Wubi.

Yep, thanks for the solution.

---

### Post by ingo on 2008-01-26
I did this and my apt-get procedure is working again. However, my system has stopped mounting usb sticks and cd roms/dvds altogether - sort of stumps me...

This is what konqueror blurts out:> Method "Mount" with signature "ssas" on interface "org.freedesktop.Hal.Device.Volume" doesn't exist?????????

---

### Post by ingo on 2008-01-26
Here is a copy of my fstab for all its worth...> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0

---

### Post by ingo on 2008-01-26
This is what made everything work again for me :)

>  sudo /usr/lib/hal/hald-generate-fdi-cache

[This bug report helped]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/139155")

---

