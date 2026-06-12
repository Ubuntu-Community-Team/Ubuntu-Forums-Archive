---
title: "Problems with mounting removable drives..!!"
date: 2007-07-12
forum: General Help
---

### Post by mrazster on 2007-07-12
Hi guys....

Not sure if this is the right section to post this...as I'm not sure if I have a hardware problem or software problem on my hands.

However...here goes.
I have been runing Xubuntu for a while now and it has been treating my good...I haven't had any problems up until now. I recently did a clean install due to an uppgrade. I did an CLI installation and then added all my packages manually thru apt. Later when I entered XFCE I kompiled kernel 2.6.22 it all went well without a glitch. 

Now my problem is that my system won't mount my dvd-rw drive or my usb drives...and if I try to mount an ISO file with *"Gmount-iso"* nothing happends.
Before the uppgrade and reinstall of OS my drives has always been automounted....did my installation in the exact same way as this time except for the kernel compilation.

I have no problem mounting my HDD.

I have tried to install *"thunar-volume-management"* but nothing happends when insert av CD/DVD or USB drive.

Gnomebaker has no problem finding and using my DVD-RW..so there's no problem there.

When I try to mount and ISO file with gmount-iso, all I get is a readme file that says something about me not having support for UDF ISO-13346

Could it have anything to do with my compiled kernel?....I followed the [_The Master Kernel Thread_](http://ubuntuforums.org/showthread.php?t=311158) howto...and didn change anything other then the recommendation in that thread..except for the ram settings. Other than that I followed it exactly.

Any help would much apreciated....!!!!!!!

---

### Post by mrazster on 2007-07-12
Anyone..???

---

### Post by mrazster on 2007-07-12
Well...thnx a bunch for all help...much appreciated. :(


However I found a solution for it.

I change the fstab line from:
```
/dev/scd0  /media/cdrom0   udf,iso9660 user,noauto  0 0
```

to:
```
/dev/scd0  /media/cdrom0   auto user,noauto,rw  0 0
```

and then rebooted.

Now it all works like a peach....somehow even the USB drives mount perfectly well.

---

### Post by minhtrietle on 2007-07-27
I have the same problem. I followed your instruction but it didn't work for my CD and DVD drives.

sad.

I spent too much time for this issue already. I didn't happen with Ubuntu 6.10

---

