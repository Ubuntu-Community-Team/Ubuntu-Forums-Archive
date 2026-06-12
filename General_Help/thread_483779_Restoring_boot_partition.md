---
title: "Restoring /boot partition"
date: 2007-06-25
forum: General Help
---

### Post by sterne on 2007-06-25
Hi,
I've been using Ubuntu for a few months now and am very happy with it.  As my hard-drive is rather small I decided to take the step of removing Windows XP entirely from my hard drive.  

Unfortunately while doing so I've managed to rubbish my /boot partition.  I've been mucking about with it for ages and things seemed to be getting worse rather than better.  Rather than boot off the live CD one more time I've installed a fresh copy of Feisty in my data partition (I've fully backed up my data so that's ok).  

My partitions are as follows:
sda1 = /boot
sda2 = oldroot with lovely well-used Feisty
sda3 = new root with fresh Feisty
sda4 = swap

Since my only problem seemed to be the /boot partition, is it possible to get the now working boot partition to boot sda2 rather than sda3?  **Where do I make this change?**

Any help much appreciated!

-------------------------------------------------------------
Possibly relevant info:
running fdisk -l /dev/sda gives:
```
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           8       64228+  83  Linux
/dev/sda2               9        1268    10120950   83  Linux
/dev/sda3            1269        4737    27864742+  83  Linux
/dev/sda4            4738        4864     1020127+  82  Linux swap / Solaris
```

My menu.lst is as follows:

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=ecc68e35-96de-49ba-a1ac-7b2de4fef227 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=ecc68e35-96de-49ba-a1ac-7b2de4fef227 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

My /etc/fstab is as follows:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ecc68e35-96de-49ba-a1ac-7b2de4fef227 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=a93656b6-c839-48ea-8362-dcb3a4517b07 /boot           ext2    defaults        0       2
# /dev/sda2
UUID=77216308-99d2-4a8a-a555-6c29ff888ed1 /media/sda2     ext3    defaults        0       2
# /dev/sda4
UUID=12877a68-d454-4dc3-befe-8772334d033d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by ikonia on 2007-06-25
are you actually getting any errors currenty? ?? have you got any problems with the data on /boot


You'll need to change various things.

Firstly - your going to need to move the data to the partition you want to be /boot.
Second: you'll need to re-install grub onto your master boot sector so that it picks up the new locations for the stage 1_5 and menu.lst files
Thirdly you'll need to update your menu.lst if you've got anything that references your old partiion in there
Finally update you fstab for the new location of /boot.

Your done.

---

### Post by Rui Pais on 2007-06-25
hi,
just edit your /boot/grub/menu.lst and add this entry:

```
title		Ubuntu, kernel 2.6.20-15-generic (sda2)
root		(hd0,0)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=77216308-99d2-4a8a-a555-6c29ff888ed1 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault
```

before the 
"title		Ubuntu, memtest86+" entry.

Check if it works.
If you wan to make it default, add a line at beginning of menu.lst:
```
default         2
```

or move the the new entry for the beginning of file.

hth



edit:
@ikonia it seems that stern had a separated boot partition, he don't need to reinstall grub... and since both they Ubuntu are feisty they use same kernels too.

---

### Post by novinthen on 2007-06-25
Hi there.

I'm having a similar problem over here.

My XP crashed earlier this week. So i installed a free XP in my C: ( ubuntu is in another partition ) . Now the loader automatically boots into XP only.  How I can re-install the loader only ?  Please help. I backed up all my data inside Ubuntu :( ... argh!!!.. :(

---

### Post by Rui Pais on 2007-06-25
> **novinthen said:**
> Hi there.

I'm having a similar problem over here.

My XP crashed earlier this week. So i installed a free XP in my C: ( ubuntu is in another partition ) . Now the loader automatically boots into XP only.  How I can re-install the loader only ?  Please help. I backed up all my data inside Ubuntu :( ... argh!!!.. :(


hi,
well your problem is completly different.
You need to recover (reinstall) grub, Windows had made the gentleness of replace it by itself alone  (rude boy, isn't it?) 

Check this how-to:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

good luck

---

### Post by r0ck80y on 2007-06-25
You just need to edit /etc/fstab :```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=ecc68e35-96de-49ba-a1ac-7b2de4fef227 **/media/sda2**   ext3   defaults,errors=remount-ro 0    1
# /dev/sda1
UUID=a93656b6-c839-48ea-8362-dcb3a4517b07 /boot           ext2    defaults        0       2
# /dev/sda2
UUID=77216308-99d2-4a8a-a555-6c29ff888ed1  **/**     ext3    defaults        0       **1**
# /dev/sda4
UUID=12877a68-d454-4dc3-befe-8772334d033d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```
The bold letters are the changes made. If the above doesn't work, then do this:```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
**/dev/sda3     /media/sda2**               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=a93656b6-c839-48ea-8362-dcb3a4517b07 /boot           ext2    defaults        0       2
# /dev/sda2
**/dev/sda2       / **    ext3    defaults        0      **1**
# /dev/sda4
UUID=12877a68-d454-4dc3-befe-8772334d033d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Note that i have given mount point for sda3 as /media/sda2. I am assuming you dont have the /media/sda3 folder

---

### Post by novinthen on 2007-06-25
> **Rui Pais said:**
> hi,
well your problem is completly different.
You need to recover (reinstall) grub, Windows had made the gentleness of replace it by itself alone  (rude boy, isn't it?) 

Check this how-to:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

good luck

Dear Rui Pais.

Thanks for the help!. Reading the help docs now. Thanks again!..:D

---

### Post by Rui Pais on 2007-06-25
hi r0ck80y.

fstab is inside the root system. 
the OP has **2** Ubuntu installed, and **2 different** fstabs :) 
he want to boot to another then the default one he needs to change the menu.lst that is on separated partition and should be general for both installations.

---

### Post by Rui Pais on 2007-06-25
> **novinthen said:**
> Dear Rui Pais.

Thanks for the help!. Reading the help docs now. Thanks again!..:D

no problem :)

btw as general information here 2 excellents HowTo on Grub:
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

good luck all.

---

### Post by sterne on 2007-06-25
Thanks Rui Pais,
I have just booted from my old setup!  I felt like a bit of a dunce when I realised what needed to be done.  The menu.lst entry root(hd0,0) had me confused into thinking that the linking happened somewhere other than menu.lst.  Of course the actual root=UUID=.... is where it all happens.

Thanks again for your time!

  -Philip.

---

### Post by r0ck80y on 2007-06-25
> **Rui Pais said:**
> hi r0ck80y.

fstab is inside the root system. 
the OP has **2** Ubuntu installed, and **2 different** fstabs :) 
he want to boot to another then the default one he needs to change the menu.lst that is on separated partition and should be general for both installations.

Ohh okay...my bad :p :P
just edit the menu.lst file as Rui Pais suggested. Thanks Rui for pointing that out :D

---

### Post by Rui Pais on 2007-06-25
> **sterne said:**
> Thanks Rui Pais,
I have just booted from my old setup!  I felt like a bit of a dunce when I realised what needed to be done.  The menu.lst entry root(hd0,0) had me confused into thinking that the linking happened somewhere other than menu.lst.  Of course the actual root=UUID=.... is where it all happens.

Thanks again for your time!

  -Philip.

Glad i could help :)

Thats the comforts of separated /boot, he he. But it has it's downsizes... 
The kernel you have in boot now is the one installed from your sda3 installation. It works with sda2 'cause they are the same, and the libs (at /lib/modules/) on sda2 are the same as sda3. 
You must be carefully when update kernels. Eventually you will have to boot to both versions and do updates for both, getting the vmlinuz on boot overwritten at the second update... 

Another option is to copy (with cp -a) then contents of /boot to one of your installs (preferentially the one not default, and change fstab and menu.lst to reflect that second boot. In that case, for that install entry (hd0,0) would change too, (as an example for (hd0,2)...)

---

### Post by Rui Pais on 2007-06-25
[QUOTE=r0ck80y]Ohh okay...my bad  :P
just edit the menu.lst file as Rui Pais suggested. Thanks Rui for pointing that out [/QUOTE]
No prob :)
I almost answer the same as you... only realize after reading a second time the 1st post. :)




(edit: don't know why when i edit my previous post to include a note to r0ck80y, forum made a second post... oh well, i edit this to avoid the duplication)

Have fun.

---

### Post by novinthen on 2007-06-25
WOW!.. that was so easy man!... I felt so scared when i didnt see the loader coming up ...

Setting up the loader as easy a ABC..

Just downloaded the SUPER GRUB DISK. Burned it as bootable disk. and run the disk. thats all :D ... thanks bunch RUI!!!!...

---

