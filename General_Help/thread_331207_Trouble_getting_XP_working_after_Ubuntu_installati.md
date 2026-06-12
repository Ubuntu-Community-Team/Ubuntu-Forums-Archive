---
title: "Trouble getting XP working after Ubuntu installation"
date: 2007-01-04
forum: General Help
---

### Post by badgaz1 on 2007-01-04
Hi I installed Ubuntu recently (dual boot with XP) and if I choose XP on the grub menu now it just says "Error 12: Invalid device requested Press any key to continue".

Anybody know how to fix that?

They are both installed on different partitions of one Harddrive, I have another harddrive as well for all my documents.

---

### Post by bodhi.zazen on 2007-01-04
Can you post the output of ```
sudo fdisk -l
``` and the windows section of /boot/grub/menu.lst

---

### Post by badgaz1 on 2007-01-04
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24222   194563183+   7  HPFS/NTFS
/dev/sda2           24223       30401    49632817+   f  W95 Ext'd (LBA)
/dev/sda5           24223       30019    46564339+  83  Linux
/dev/sda6           30020       30401     3068383+  82  Linux swap / Solaris

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/hda5               2       24321   195350368+  83  Linux



Is this the right part?

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by bodhi.zazen on 2007-01-04
Yes, that is the information we need to help you :p

I think you need to change

root (hd0,1)

to

root (hd0,0)

---

### Post by badgaz1 on 2007-01-04
Thanks for the help but now it just says "Starting up..." or something like that and never actually...starts up lol.

It's strange though because if I insert the Ubuntu disk and go on "boot from first disk drive" and choose XP it starts up no problem. ](*,)

---

### Post by bodhi.zazen on 2007-01-04
Try commenting out the mapping lines. Add a # in the front of them like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Professional
root (hd0,1)
savedefault
makeactive
# map (hd0) (hd1)
# map (hd1) (hd0)
chainloader +1

---

