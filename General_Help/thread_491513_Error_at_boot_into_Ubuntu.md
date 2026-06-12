---
title: "Error at boot into Ubuntu"
date: 2007-07-03
forum: General Help
---

### Post by fumduck on 2007-07-03
Just before Ubuntu goes to login , I get this error.



Log of fsck -C -R -A -a 
Tue Jul  3 17:53:03 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Wrong checksum for long file name "11 :FyH:FyG:300:Fya:Fyl:Fyi:Fyi:FyX:Fyo.mp3".
  (Short name FSCK0000.REN may have changed without updating the long name)
  Not auto-correcting this.
/dev/sdb1: 22621 files, 4750250/7204643 clusters
/dev/sdb2: clean, 26195/3842720 files, 3733750/7679070 blocks
fsck.ext3: Unable to resolve 'UUID=f0845e1a-f14c-4cc5-99cc-ca676420146c'

fsck died with exit status 8

Tue Jul  3 17:52:48 2007


 And I don't know hot to fix this.. I basically have to hit ctrl d everytime and then it boots into it fine.  None of my partitions have this uuid??  Is this like one on my dvd or cd drives?/ they both work?? Would appreciate help.. Thank you in advance:p

---

### Post by raja on 2007-07-03
Can you post your /etc/fstab ?

---

### Post by Juan_VCS on 2007-07-03
Edit your grub menu list file accordingly (/boot/grub/menu.lst)

---

### Post by fumduck on 2007-07-03
info is I have two sata hds... 1 has (in order)  Fiesty,XP, LinuxOS,and Vista  2nd.. has /home, swap, and  a backup partition in vfat... and menu.lst I have looked and done update grub, but really nothing looks wrong??




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cabcea8e-e0ce-4a50-8bd3-d4e063436d9a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb2
UUID=ff20a57d-bda3-4810-86fe-ab8853eb06d1 /home           ext3    defaults        0       2
# /dev/sda2
UUID=660C0DC50C0D90EB /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=f0845e1a-f14c-4cc5-99cc-ca676420146c /media/sda4     ext3    defaults        0       2
# /dev/sdb1
UUID=4659-7823  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=f32c9d8a-7bd7-4719-a010-e26b0dac7f5f none            swap    sw              0       0
# /dev/sdb3
UUID=40df25fe-26b3-4105-bc37-1eb5c0962eeb none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda4    is that the same order as partions created?? Because if so it should be ntfs?? (vista)  But I also thought the drive was sdb1.. order in sata plugs on MB

---

### Post by raja on 2007-07-03
I would change the last column to 2 for all listings except for the root partition. If there are still problems with fsck for the fat partition, just change the last column to 0 to disable file checking.

---

### Post by fumduck on 2007-07-04
I am sorry , I don't quite get what you meant. I am just learning computers, and linux.. Its a hobby.. No real background here other than what I can read on forums..  Are you saying editing the ect/fstab ??  If so can you copy and paste what I have above, and example what should be left?? So as I don't do any big harm..because it is alittle confusing.. because the sda and sdb don't seem to follow my partitions I created?? I think I may have to look again..

---

### Post by Nythain on 2007-07-04
try replacing
UUID=f0845e1a-f14c-4cc5-99cc-ca676420146c
with
/dev/sda4
in your /boot/grub/menu.lst and see if that works
sounds like the uuid of the drive changed but grub didnt pick it up, so now its trying to mount a device it doesnt think exists

---

### Post by Nythain on 2007-07-04
> **fumduck said:**
> info is I have two sata hds... 1 has (in order)  Fiesty,XP, LinuxOS,and Vista  2nd.. has /home, swap, and  a backup partition in vfat... and menu.lst I have looked and done update grub, but really nothing looks wrong??




# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=cabcea8e-e0ce-4a50-8bd3-d4e063436d9a /               ext3    defaults,errors=remount-ro 0       1
this appears to be the first partition you created on your first had drive, and mounted at /
> # /dev/sdb2
UUID=ff20a57d-bda3-4810-86fe-ab8853eb06d1 /home           ext3    defaults        0       2
this would be the second partition you created on your second drive and is mounted at /home
> # /dev/sda2
UUID=660C0DC50C0D90EB /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
this is the second partition on your first hard drive, wich is in ntfs format, and you have mounted at /media/sda2 (im assuming its an xp partition of some sorts
> # /dev/sda4
UUID=f0845e1a-f14c-4cc5-99cc-ca676420146c /media/sda4     ext3    defaults        0       2
this would be the problem partition from what i can gather and you should change this to look like
```

/dev/sda4   /media/sda4   ext3   defaults   0  2

```
> # /dev/sdb1
UUID=4659-7823  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
this is the first partition on the second hard drive using fat32 (another windows partition, or a partition to transfer data between the two os's i assume)
> # /dev/sda3
UUID=f32c9d8a-7bd7-4719-a010-e26b0dac7f5f none            swap    sw              0       0
the third partition created on the first disk, a swap partition
> # /dev/sdb3
UUID=40df25fe-26b3-4105-bc37-1eb5c0962eeb none            swap    sw              0       0
the third partition created on the second disk, ALSO A SWAP???  why two swaps???
> /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
these are pretty self explanatory

---

### Post by raja on 2007-07-04
> **Nythain said:**
> 
sounds like the uuid of the drive changed but grub didnt pick it up, so now its trying to mount a device it doesnt think exists

Definitely possible. But you can check the UUIDs in the fstab against what you get with ```
ls -l /dev/disk/by-uuid
```

Maybe better than changing everything. As you pointed out, two swaps are not needed and he can take off one of those from the fstab and later format and mount it elsewhere.

---

### Post by fumduck on 2007-07-04
the third partition created on the first disk, a swap partition
the third partition created on the second disk, ALSO A SWAP???  why two swaps???

3rd partition  on first drive is Pclinux os  
and this is my menu.lst


## ## End Default Options ##

t
title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cabcea8e-e0ce-4a50-8bd3-d4e063436d9a ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=cabcea8e-e0ce-4a50-8bd3-d4e063436d9a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP/ Vista
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title linux
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sda3  acpi=on resume=/dev/sdb3 splash=silent vga=788
initrd (hd0,2)/boot/initrd.img

title linux-nonfb
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sda3  acpi=on resume=/dev/sdb3
initrd (hd0,2)/boot/initrd.img

title failsafe
kernel (hd0,2)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sda3  failsafe acpi=on resume=/dev/sdb3
initrd (hd0,2)/boot/initrd.img

 and Sda4 should be Vista..
I guess I'll try editing the fstab??
 
Thank you all for the help so far

---

### Post by fumduck on 2007-07-04
ok fixed it.. changed ext3 to Ntfs in  fstab.. should vista and xp have the same options after the ntfs in fstab?? 
XP
# /dev/sda2
UUID=660C0DC50C0D90EB /media/sda2 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
Vista
# /dev/sda4
UUID=f0845e1a-f14c-4cc5-99cc-ca676420146c /media/sda4 ext3 defaults 0 2

 I know that when I tried to make a  vista boot option in menu.lst it never worked .. but I have a boot option that brings me to a windows boot option.. So I can get into everything.. But just wondering.. 
Thank you all so much this community is great, and its becasue of all of you.

Peace
M.R.

---

