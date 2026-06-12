---
title: "[SOLVED] Dual boot to Single boot"
date: 2007-12-03
forum: General Help
---

### Post by Don DeGregori on 2007-12-03
Have computer that is supposed to boot from USB. 7.10 is on internal HD. Decided to try it. Put in LiveCD for 7.04 with external USB HD connected. Did the Install OK and now have dual boot with 7.04 as 1st choice, and 7.10 as 2nd.  All works, but now of course if I unplug the USB HD, and try to boot, I get a GRUB error 21, saying "where is the USB HD?" And I'm saying "why did didn't realize this?" So, dual boot works, but I want to go back to single boot with just 7.10. How do I do this? I'm sure this has been asked before, but could someone lead me by the hand?

Thanks, Don

---

### Post by teryowen on 2007-12-03
boot of live cd

in terminal do this:

sudo fdisk -l

post the output.

OR

if you know which partition your ubuntu is on do the following from the live CD:

sudo grub
root (hd0,X)
setup (hd0)
quit

Where X is the partition Ubuntu is on so if its on the 1st paritions (say sda1) X=0 if on the 2nd (say sda1) X=1  and so on

---

### Post by Don DeGregori on 2007-12-03
Here is what fdisk -l says

donde@donde-desktop:~$ sudo fdisk -l
[sudo] password for donde:
Sorry, try again.
[sudo] password for donde:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb8ccb8c

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1824    14651248+  83  Linux
/dev/hda2            1825        1948      996030   82  Linux swap / Solaris

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73d541c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1824    14651248+  83  Linux
/dev/sda2            1825        1948      996030   82  Linux swap / Solaris
donde@donde-desktop:~$ 


hda is what I want to single boot to.

Don

---

### Post by teryowen on 2007-12-03
alright do this in terminal:

```

sudo grub
root (hd0,0)
setup (hd0)
quit
```

tell me how it goes.

---

### Post by Don DeGregori on 2007-12-03
That did the trick. Thanks so much. Now, with the USB HD unplugged, 7.10 boots fine. 
Can I use this line of code to put back dual boot? Of course changing the parameters.

Appreciate the help...Don

---

### Post by teryowen on 2007-12-03
Yap definitely, if you want to use the grub file on another hard drive change the commands a bit like so:

grub sudo
root (hdY,X)
setup (hdY)
quit

Where Y is the hard drive so sda sdb would be different hard drives as well hda and hdb would be different same with hda and sda are also different and require different Y values. Y starts at 0, zero beign the first hard drive 1 being the second and so on.

Where X is the partition on the specific hard drive so sda1 or sdb1 or hda1 or hdb1 all have the same partition. X starts at Zero ( 0 ) being the first partition and one (1) being the second and so on.

So if you want to set it up on a different hard drive or partition change the X and Y values.

But my suggestion would be to look at the menu.lst file from the external hard drive and add the entry from of the external hard drive to the menu.lst file on the inertial one, that way GRUB is set up on the internal you can choose the external but nothing will happen unless its plugged in at the same time if its not plugged in you can still use ur internal.

---

### Post by Don DeGregori on 2007-12-03
I'll print all that happened. I can see how much I need to bone up on GRUB. It's a powerful application. People like you really make this forum worth while, even though is some misinformation from others. I'll post [SOLVED] 
Thanks, Don

---

