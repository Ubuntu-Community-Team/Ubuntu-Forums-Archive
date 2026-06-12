---
title: "Ubuntu boot hangs after xp install and shutdown"
date: 2007-05-29
forum: General Help
---

### Post by killroy on 2007-05-29
Ok, to explain a little better:  My xp disk has somehow been messed up and has not been able to boot (gets to loading screen, then the wonderful blue screen and reboots) so I resize the disk and add another partition to it, installing xp on the new part.  Meanwhile, i'm still trying to boot the defective xp part, using fixboot, fixmbr with no success.  I can **only** boot in safemode with networking, no other way.  Though I don't care all that much about my xp install, I would like to get my ubuntu install working again.  The problem is my grub loads fine, I select my os and it hangs at the loading (with the progress bar at the minimal level) then after a few minutes it gets an error of "/bin/sh: can't access tty; job control turned off".  I've reinstalled grub, so i'm pretty confident that it isn't the problem.  Also, I do have 2 sata drives and 1 ata, but they were all working properly before the xp error/install.

Specs: amd 64 3800+
2 sata drives (80gb each) -xp, storage
1 ata drive (40gb) -ubuntu
1 dvd-rom
512ram

If any more information is needed, please tell me.  Thanks for any help.

Edit: a screenshot of loading: [http://librarian.launchpad.net/7176525/ubuntu-6.06-splash-progress.jpg](http://librarian.launchpad.net/7176525/ubuntu-6.06-splash-progress.jpg)

---

### Post by 1/0 on 2007-05-29
Well, I'll try to give you a start. "/bin/sh: can't access tty; job control turned off" is probably not the problem but just a general notice. Try turning off the splash screen by deleting "splash quiet" from GRUB and you'll get more to go with. 

Ubuntu worked before all this right? Is GRUB pointing to the correct drive/partitions? Are the jumpers set correctly on the drives?

---

### Post by killroy on 2007-05-29
Yes, Ubuntu was working fine.  Jumpers haven't been messed with, so they should be fine.  GRUB is fine, I think.  I'll try deleting splash quiet and see what happens.

Edit:  OK, deleted "splash quite".  The error i'm getting is: 
"Check root=bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls dev
ALERT! /dev/disk/by-uuid/ee884b3-c4f2-418d-8010-5aa44b5f4e8b does not exist.  Dropping to a shell!"

So i'm thinking you were right, that maybe grub isn't pointing to the correct partition?  Or is it something else?

---

### Post by killroy on 2007-05-29
I've tried to see if the drive somehow has a new uuid by typing 'sudo vol_id -u /dev/hdb1' but it does nothing; 
ubuntu@ubuntu:~$ sudo vol_id -u /dev/hdb1
ubuntu@ubuntu:~$ 

I also cannot see the drive in /dev/disk/by-uuid, but I can see all the others (windows, and even hdb5 swap).  Would GRUB work with using /dev/hdb1, instead of the uuid?  I know I can just reformat and reinstall, but then i'd lose all my electronic belongings and settings. :(
Anyone?  Anyone?

---

### Post by confused57 on 2007-05-29
> **killroy said:**
> I've tried to see if the drive somehow has a new uuid by typing 'sudo vol_id -u /dev/hdb1' but it does nothing; 
ubuntu@ubuntu:~$ sudo vol_id -u /dev/hdb1
ubuntu@ubuntu:~$ 

I also cannot see the drive in /dev/disk/by-uuid, but I can see all the others (windows, and even hdb5 swap).  Would GRUB work with using /dev/hdb1, instead of the uuid?  I know I can just reformat and reinstall, but then i'd lose all my electronic belongings and settings. :(
Anyone?  Anyone?
The UUID for whichever partition you resized has probably changed.  You should be able to edit your fstab & menu.lst and enter the correct UUID, using the live cd:
Open a terminal and determine your new UUID(s):
```
blkid
```

Then you'll need to mount your root partition and make the necessary changes:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda1 /media/ubuntu
```
you can determine which is your root partition with:
```
sudo fdisk -l
```
the -l is a small "L"

Substiture the hda1 according to the results of "fdisk -l".

Then to edit your menu.lst & fstab:
```
gksudo gedit /media/ubuntu/etc/fstab
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

You can probably just copy & paste the UUID from "blkid" into your menu.lst kernel line & your fstab entry.

Added:  Unless you resized your root partition, your menu.lst kernel line UUID should be correct & you shouldn't need to edit.

---

### Post by killroy on 2007-05-30
Thanks for the reply, confused57.  I tried what you said, using blkid to find my linux disks uuid.  When I did, it gave me the exact same uuid as in my menu.list and fstab, thus giving me the same error when I try to load ubuntu.  I've not resized my linux part since I installed it, so it shouldn't have changed. (at least in my mind anyway)

Edit:  Trying to be smart here, I was examining the error message and decided to see what was in the /proc/modules on my harddrive with ubuntu installed... and nothing is in it.  I'm guessing something should be in it, because on the live cd (which is what i'm using) it has a list of folders and files.  Is this normal?  Can I just copy the directory from the live cd to the harddisk and hope it will work?

---

### Post by confused57 on 2007-05-30
> **killroy said:**
> Thanks for the reply, confused57.  I tried what you said, using blkid to find my linux disks uuid.  When I did, it gave me the exact same uuid as in my menu.list and fstab, thus giving me the same error when I try to load ubuntu.  I've not resized my linux part since I installed it, so it shouldn't have changed.

I suppose you could try substituting /dev/hda1, or whatever your Ubuntu partition is in your fstab & kernel line.
Open a terminal & determine how your root partition & swap partition are identified:
```
sudo fdisk -l
```
the -l is a small "L"

Here is my Dapper fstab:
```
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
```

and Dapper menu.lst:
```
title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot
```

It would be worth trying...Did running blkid show your UUID as?:
> ALERT! /dev/disk/by-uuid/ee884b3-c4f2-418d-8010-5aa44b5f4e8b does not exist. Dropping to a shell

---

### Post by killroy on 2007-05-30
> It would be worth trying...Did running blkid show your UUID as?:
[QUOTE]ALERT! /dev/disk/by-uuid/ee884b3-c4f2-418d-8010-5aa44b5f4e8b does not exist. Dropping to a shell
[/QUOTE]

Yes, it's the same.  Results of blkid:
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: TYPE="ntfs" 
/dev/sdb1: TYPE="ntfs" 
/dev/hdb1: UUID="ee8845b3-c4f2-418d-8010-5aa44b5f4e8b" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdb5: UUID="684025b0-915f-40c0-98be-00eb46777f08" TYPE="swap"

---

### Post by killroy on 2007-05-30
It worked!  I copied /proc from the live cd over my disks /proc (which had nothing in it), restarted, edited my grub kernel (deleting, quiet & splash) then a forced disk check occured which I recieved an error and the comp restarted, then to grub again, edited the command line from
"kernel                   /boot/vmlinuz-2.6.20-15-generic root=UUID=ee8845b3-c4f2-418d-8010-5aa44b5f4e8b ro quiet splash"  to  "/boot/vmlinuz-2.6.20-15-generic root=/dev/hdb1 ro"
And so far all is working fine.  Thanks again for your help, 1/0 and confused57.

---

