---
title: "GRUB dissapears"
date: 2007-03-29
forum: General Help
---

### Post by numiller on 2007-03-29
Hello,  I have had issues with grub.

I have a sata drive with xp and ubuntu and an IDE drive that is storage.  The original install put GRUB onto the IDE drive.  This is fine as I can switch the boot drive to go into XP if i want to.  However, every time i shut down, completely power off, grub seems to disappear.  I then need to run the live cd and reinstall grub to the IDE drive.  After doing that i can restart just fine into either ubuntu or XP.  If i leave the PC off for a bit then the boot up doesn't work.  I have tried installing grub to the SATA drive but that resulted in neither xp or ubuntu working (did get the grub menu though).

Extra info:

I cannot mount the IDE drive in linux.

fdisk -l output:

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6272    50379808+   7  HPFS/NTFS
/dev/sda2            7650       36482   231601072+   f  W95 Ext'd (LBA)
/dev/sda3            6273        7583    10530607+  83  Linux
/dev/sda4            7584        7649      530145   82  Linux swap / Solaris
/dev/sda5            7650       36482   231601041    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/hdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        7476    60050938+  42  SFS

fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=62a71bbf-0a62-4034-8636-ad30af575ac6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd1
UUID=2440904B40902618 /media/hdd1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=845C1FF05C1FDBAC /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=08603164603159A0 /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=8be37b9f-2f08-47e2-bfa6-39628da3315d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Any help would be great

---

### Post by nixclusive on 2007-03-30
Can you paste the contents of the file menu.lst? -- /boot/grub/menu.lst

>> I have tried installing grub to the SATA drive but that resulted in neither xp or ubuntu working (did get the grub menu though).

in the menu, press 'e' to edit the entries temporarily and try changing the 'root' command.

---

### Post by numiller on 2007-03-30
thanks for the reply.

here are the contents from the menu.lst [booted through the IDE drvie]


title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


I tried installing on the SATA drive again with the same result.  I tried editing what partition it points to but it didn't work.  from the "command line" in grub i redid the steps i do to install grub off the live cd

```
find /boot/grub/stage1

root (hdx,x)

setup (hd0)
```

the find command normally returnd hd1,2 when using the live cd.   I then install grub to hd1.  When i reboot I change the HDD boot order to the SATA drive.  After this the find command returns hd0,2.  So i try installing again with that information.  It doesn't work after i reboot the 'edit list still shows "root (hd1,2).  If i manually add "root (hd0,2)" and try booting it say partition does not exist.  Not sure on what else to try doing.  Have to load the live cd every time i shut down isn't very fun.

---

### Post by nixclusive on 2007-03-31
Oh,,k now looks like you have linux installed in /dev/sda3 and windows in /dev/sda1. Now lets try re-installing grub step-by-step from the live cd.

1. Load and boot the live CD......... yeah it sure is a long wait.
2. Open the terminal in the live cd and start punching:```
sudo mount /dev/sda3 /mnt/
cd /mnt
```
3. Make sure the boot/grub directory structure is here:```
ls boot/
```
4. Install grub directing it here to find the stage2 files here:```
sudo grub-install --root-directory=/mnt/
```
5. It should come up with something like XFS Freeze.. blah.. blah.. blah.. and a listing of what is contained the file device.map This file contains the grub's point of view of what is what and where is where. 

Try restarting the computer without the live cd. Let us know if it worked..

---

### Post by numiller on 2007-04-04
well, I have not tried the last bit of advice as now my pc is booting fine after long periods of being off (last 2 days almost).  No idea what changed (i did install the NTSF write support program).  Oh well, some fluke happening the first couple times i guess (knocks on wood).

Thanks for your help

---

### Post by nixclusive on 2007-04-05
anytime.. good to see people reporting a problem solved. thank you.

---

