---
title: "rezied partion, lost Wubi"
date: 2008-06-03
forum: General Help
---

### Post by darco on 2008-06-03
I resized an unused portion of my C: drive and I guess I borked the mbr. I was able to recover and succesfully boot back into windows but when I try to access Ubuntu from the boot menu I get " \ubuntu\winboot\wubildr.mbr" that its missing or corrupt.. I am going to try SuperGrub later today as I have to head out to work. Is this the correct path to go?
thxs
darco

---

### Post by ago on 2008-06-03
Wubi uses a UUID number to identify partitions, if that is changed it will not be able to find one. You will have to replace said UUID in c:/ubuntu/disks/boot/grub/menu.lst with the appropriate device (e.g. /dev/sda1)

---

### Post by darco on 2008-06-03
> **ago said:**
> Wubi uses a UUID number to identify partitions, if that is changed it will not be able to find one. You will have to replace said UUID in c:/ubuntu/disks/boot/grub/menu.lst with the appropriate device (e.g. /dev/sda1)

Ago, here is the current menu.lst:


title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic

So I need to change the UID to /dev/sda1 like below?


title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-17-generic root=/dev/sda1/ loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic

Wow, I really couldnt spell this morning "rezied partion". I gues the carafe of beans I have isnt enough!
thxs
darco

---

### Post by ago on 2008-06-04
Assuming you installed on the first partition of the first hard disk yes, otherwise it will be /dev/sda2 (disk 1 partition 2) or /dev/sdb1 (second disk partition 1) or whatever is appropriate

You can also find out the new UUID by using

ls -l /dev/disk/by-uuid

---

### Post by darco on 2008-06-04
> **ago said:**
> Assuming you installed on the first partition of the first hard disk yes, otherwise it will be /dev/sda2 (disk 1 partition 2) or /dev/sdb1 (second disk partition 1) or whatever is appropriate

You can also find out the new UUID by using

ls -l /dev/disk/by-uuid

Well I am not getting anywhere here...
This is the output for by-uuid:
lrwxrwxrwx 1 root root 10 2008-06-04 08:01 685691975691669A ->../../sda2

lrwxrwxrwx 1 root root 10 2008-06-04 08:01 A23869263868FAA5 -> ../../sdb1
 
lrxrwxrwx  1 root root 10 2008-06-04 08:01 C684A28884A27B17 -> ../../sda1

I have one HDD, with 3 partitions and I external drive.
Ubuntu is loaded on the first partition. One of the partitions is unused

The UUID for the partition has not changed if you look at my previous post showing the UUID.
I did try entering sda2 but I cannot log in, still getting the original error message.
I know I must be overlooking something....
thxs
darco

---

### Post by ago on 2008-06-04
Well it looks you have 2 disks, not one (one might be a flash drive or something).

In such case might be an issue unrelated to the UUID

You might want to edit menu.lst following these instructions:

[https://wiki.ubuntu.com/WubiGuide#head-d21adc0c698b89c9cc354d1c6d945aabac5d7904](https://wiki.ubuntu.com/WubiGuide#head-d21adc0c698b89c9cc354d1c6d945aabac5d7904)

> edit c:\ubuntu\disks\boot\grub\menu.lst. You have to change all the lines "root (hdX,Y)/ubuntu/disks" to "root ()/ubuntu/disks". Also edit the line that starts with "#groot=(hdX,Y)/ubuntu/disks" to "#groot=()/ubuntu/disks".


title Ubuntu 8.04, kernel 2.6.24-17-generic
**root ()/ubuntu/disks**
kernel /boot/vmlinuz-2.6.24-17-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.24-17-generic


...and if you installed on a fat partition it might be another issue still (boot with the -16 kernel)...

---

### Post by darco on 2008-06-04
Still unable to log in.....do I need to uncomment out the # groot=()/ubuntu/disks?
No FAT here!
thanks


## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks


## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-15-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu 8.04, kernel 2.6.24-15-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-15-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-15-generic

title		Ubuntu 8.04, kernel 2.6.24-14-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu 8.04, kernel 2.6.24-14-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-14-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-14-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, kernel 2.6.24-12-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=C684A28884A27B17 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-12-generic

title		Ubuntu 8.04, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
chainloader	+1

---

### Post by ago on 2008-06-04
menu.lst is fine. Boot in rescue mode with the 16 kernel (possibly adding "debug=2" as boot option)

Then provide the log in /tmp

---

### Post by darco on 2008-06-04
Not sure how to get to rescue mode since Ubuntu never loads. I didnt see an option w/the Live CD.

darco

---

### Post by ago on 2008-06-04
what happens if you press esc at boot after ubuntu? you should be able to select rescue mode kernel 16

---

### Post by darco on 2008-06-04
I get the Windows Boot Manager on boot up. Now the order has changed where in the past Windows was on top and Ubuntu was below, now its the other way around. When I choose Ubuntu, it immediately goes to the error above.
thxs
darco

---

### Post by ago on 2008-06-05
Hmm I didn't notice it was a grub4dos issue from your first post... Sorry I was heading in a different direction.

Looks like you cannot load wubildr.mbr at all

Check that the file is in C:\ and C:\ubuntu\winboot. You can remove all traces of wubildr*, use the newest version of grub4dos into C:\ , change your bootloader accordingly, and copy c:\ubuntu\winboot\menu.lst into C:\

---

