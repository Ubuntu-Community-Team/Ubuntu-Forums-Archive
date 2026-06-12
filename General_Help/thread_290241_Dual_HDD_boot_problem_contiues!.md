---
title: "Dual HDD boot problem contiues!"
date: 2006-10-31
forum: General Help
---

### Post by badguyanil on 2006-10-31
Guys i have posted this earlier in some threads but did nto get any reply there!
ok guys i am a bit confused. this is wht i did, can u tell me how and why is it not working.

I have 2 hdd's 20 GB and 40 GB.
1.40 GB has Win XP and Win 98 installed and was the master drive.
2.I disconnected this drive. Connected 20 GB as Master(Hdd jumper settings) and installed Ubuntu(6.10)...smooth!
3. Conencted back windows drive (40 GB) as slave(HDD jumper setting).

now i can boot from either of the HDD by connecting and disconnecting the power cable and and checking thru bios once!

4.With both the HDD's connected (Ubuntu master, Win (XP + 9 Slave), if i try to boot it boots up ubuntu! Well that is wht it shld do.

5. In grub menu.lst i made the entries...

title Windows
.
.
chainloader +1
just above the entiers of Ubuntu...(##Entries for automatic...)
and have also tried pasting it below the after the Ubuntu boot entires (##End of Debian....)

Now the Problem :... when i boot up i get the menu asking me to choose between Windows and Ubuntu. But when i select Windows..i get the error "Error : Unrecognised Device String". What shld i do??????

I want to keep ubuntu as master!..Please help!

When i run $sudo fdisk -l 
i get the hdds as 
hdaX... for ubuntu
hdbX... for the windows drives

Also let me know how to mount the windows drives on Ubuntu.. I have refered to some of the threads but did nto get much help.

---

### Post by confused57 on 2006-11-01
Have you tried a Windows entry in /boot/menu.lst similar to the one in this thread?:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by badguyanil on 2006-11-01
oh ya entry taken from that very thread...
anyways this is wht the entry in the menu.lst file is 

title              Windows
rootnoverify      (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

i guess i forgot to mention i use ubuntu 6.10.. tha is any ways not gona make any diff i guess. Tried with "root" instead of "rootnoverify" too!

---

### Post by confused57 on 2006-11-01
Here's how to mount Windows from Ubuntu:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

It would help if you could post(copy&paste) the complete output of:
```
sudo fdisk -l
```

---

### Post by badguyanil on 2006-11-01
> **confused57 said:**
> Here's how to mount Windows from Ubuntu:
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

It would help if you could post(copy&paste) the complete output of:
```
sudo fdisk -l
```

Will post the output od fdisk in a few hrs...
Can u tell me wht these are for!

```
ntfs nls=utf8,umask=0222 0 0
vfat iocharset=utf8,umask=000 0 0
```

taken from the link u directed me to! i followed the instructions from there but no luck! :-k

---

### Post by badguyanil on 2006-11-01
Well here goes the fdisk output more or less the same:

Disk /dev/hda: 20.0 G....
Device Boot Start....
/dev/hda1 * ...........................Linux
/dev/hda2 .............................Extended
/dev/hda5 .............................Linux swap...

Disk /dev/hdb: 40.0 G....
Device Boot Start....
/dev/hdb1 * ...........................W95 FAT32
/dev/hdb2 .............................W95 Ext'd (LBA)
/dev/hdb5 .............................W95 FAT32
/dev/hdb6 .............................W95 FAT32
/dev/hdb7 .............................W95 FAT32
/dev/hdb8 .............................W95 FAT32

if u want the exact contents well can post it only in another 8-9hrs...post office timings!

---

### Post by badguyanil on 2006-11-01
i guess i need to send the complete list as is ! This is becoming a huge prob guys...for everytime i need to load windows i need to unplug the power cable of that hdd! Please help!

---

### Post by confused57 on 2006-11-01
You might be able to use the Super Grub Disk to boot your Windows drive:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

At the bottom half of the homepage of the above website there is a index link to SGD and there's also some excellent links explaining grub, GAG bootloader, how to mount partitions, etc.
The mount partitions section explains how to temporarily mount your Windows partition(s) without adding anything to your fstab, which would mount the partition everytime you boot Windows.
   Looks like all your Windows partitions are formatted as FAT32...usually Windows XP is formatted as ntfs.  Linux is able to write to FAT32, but not ntfs.
   The Windows entry "should" boot your hdb drive, are you typing the command or copy & pasting to your menu.lst?  Try copy & pasting, if you haven't already.  Make sure your jumper setting is for "slave" or "cable select", if supported, for the Windows drive...

---

### Post by badguyanil on 2006-11-01
Well here goes the fdisk output more or less the same :

Disk /dev/hda: 20.4 GB
Device        Boot   ...    System
/dev/hda1     *             Linux
/dev/hda2                   Extended
/dev/hda5                   Linux Swap/Solaris

Disk /dev/hdb: 40.0 GB
Device        Boot   ...    System
/dev/hdb1     *             W95 Fat32
/dev/hdb2                   W95 Ext'd(LBA)
/dev/hdb5                   W95 Fat32
/dev/hdb6                   W95 Fat32
/dev/hdb7                   W95 Fat32
/dev/hdb8                   W95 Fat32

And well ya i set all the drives as FAt as i use it at my home and is a single user system so dont ned to maintain the file level permissions and all. 

Now can someone tell me how to:
1... Make entires in /boot/grub/menu.lst so that i can dual boot!
2... Make entries in /etc/fstab so that i can mount these drives in linux too.

---

### Post by matthewstory on 2006-11-01
well in menu.lst, a couple things, you need to make sure first that the right disk is specified near the top of menu.lst:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda6 ro

you'll need to make sure that last line is set to the right disk and partition.  Keep the # delimiter there, it is very stupid on the part of the grub developers, but this is not a comment.

Next:

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title           Microsoft Windows XP Home Edition
root            (hd0,1)
savedefault
makeactive
chainloader     +1

This is of course, for a dual boot with one disk, assuming hd0 is linux and hd1 is windows your windows part should look like this:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
chainloader     +1

hope this helps.

---

### Post by matthewstory on 2006-11-01
A note on the above post:

This above post was taken off of a working single disk dual boot Windows XP HE/Breezy Install, my Dapper box isn't dual boot, so the kernel images and stuff are all off for Dapper of Edgy

---

### Post by badguyanil on 2006-11-03
can any one with a similar setup of hdd's post the contents of menu.lst plz! 
Config again:
Ubunto 6.10     (primary master)
Windows XP+98   (primary slave )

---

### Post by badguyanil on 2006-11-04
Does any one has the above mentioned setup! Please reply!

---

