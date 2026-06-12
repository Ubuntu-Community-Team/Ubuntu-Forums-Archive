---
title: "Install Ubuntu Gnome to Correct Partition"
date: 2017-02-08
forum: General Help
---

### Post by webmanoffesto on 2017-02-08
According to Disk Utility my HD is correctly partitioned for a Linux installation. 
- Main Partition: 926 GB ext4
- 74 GB Extended
- 20 GB ext4
- 54 GB Swap space

If I recall correctly, the last time I reinstalled my Linux OS I accidentally installed the OS into the Main partition.

1. How do I install Ubuntu Gnome 16 from a Live Disk and make sure the OS goes to the correct partitions? 
Note that it may detect an Ubuntu installation in the Main partition and offer to put the new OS there.

2. What folders and files can I remove from the Main partition after I put the OS where it should be?

---

### Post by Bashing-om on 2017-02-08
webmanoffesto; Hello;

Show us the partitioning on the drive(s).
Post back - Between code tags - the outputs of terminal commands:
```

sudo parted -l
sudo fdisk -lu

```
And we then know what to start looking for .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2017-02-08
You would choose 'Something Else' at the partitioning section of the install and manually partition. Can't give you much details on much else as no idea what you've got installed where to start with as you don't say. ;)

Ninja-ed. Yea, as Bashing-Om said ...

---

### Post by webmanoffesto on 2017-02-08
```

> sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002d4c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1808337985   904167969   83  Linux
/dev/sda2      1808338942  1953523711    72592385    5  Extended
/dev/sda5      1808338944  1847400447    19530752   83  Linux
/dev/sda6      1847402496  1953523711    53060608   82  Linux swap / Solaris



```

---

### Post by Bashing-om on 2017-02-08
webmanoffesto; hey hey ..

The 2 linux partitions are identified, now which is which that you want to replace ? ( labels sure are nice ) 
You can "look' and make a determination on which one to replace.what returns :
```

mount
lsb_release -a

```
From this we know which partition is booted .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by webmanoffesto on 2017-02-08
It seems to me that

Device      Boot     Start End          Blocks      Id  System
/dev/sda1   *        2048  1808337985   904167969   83  Linux

Is the largest partition, and the "*" says that it is now (accidentally) the boot partition.

The other partitions should have nothing on them. How do I make sure my next Linux install puts the OS there.

Can you be more exact.
I didn't understand how to mount and explore the other partitions. 
I booted off of SDA1 and my data is there too.
How do I mount and view SDA2

```

tom@TomsAsusK55A:~$ mount /dev/sda2
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab

```

---

### Post by Bashing-om on 2017-02-08
webmanoffesto; Sorry;

My communications skills often leave a lot to be desired.
In terminal execute terminal command:
```

mount

```
This shows all that the  system has mounted, and among all this is the device and root partition currently mounted.
This will confirm that " I booted off of SDA1 and my data is there too." .
 

Assuming that you are in fact booted from sda1; to access the sda5 linux partition :
execute in terminal:
```

sudo mkdir /mnt/looksee
sudo mount /dev/sda5 /mnt/looksee
ls -al /mnt/looksee
ls -al /mnt/looksee/home

```
be aware that sda2 is an 'extended' partition . This is but a container to hold other 'logical' (sda5 sda6) partitions. It has no data in and of it's self .

When all done looking around you MUST UNmount sda5 . You mounted it and the system expects you to take responsibility for it.

When all done UNmount :
```

sudo umount /dev/sda5

```

[INDENT][INDENT]easy as falling out of bed wide awake
[/INDENT][/INDENT]

---

### Post by webmanoffesto on 2017-02-08
The "install a different way" install option brings me to the re-partition screen, which shows me
[FONT=courier new]/dev/sda
   /dev/sda1   ext4   925868 MB   Debian Gnu Linux (7.11)
   /dev/sda5   ext4    19999 MB   Ubuntu 16.04 LTS
   /dev/sda6   swap    54334 MB   unknown    [/FONT]

[http://imgur.com/a/JoTFz](http://imgur.com/a/JoTFz)

So I guess, if I manage to boot off of sda5 I would boot into Ubuntu 16.04, and I'd be using sda6 as my Swap Disk. How do I set my laptop to boot off of sda5?

---

### Post by Bashing-om on 2017-02-08
webmanoffesto' Hummm //

> **webmanoffesto said:**
> The "install a different way" install option brings me to the re-partition screen, which shows me
[FONT=courier new]/dev/sda
   /dev/sda1   ext4   925868 MB   Debian Gnu Linux (7.11)
   /dev/sda5   ext4    19999 MB   Ubuntu 16.04 LTS
   /dev/sda6   swap    54334 MB   unknown    [/FONT]

[http://imgur.com/a/JoTFz](http://imgur.com/a/JoTFz)

So I guess, if I manage to boot off of sda5 I would boot into Ubuntu 16.04, and I'd be using sda6 as my Swap Disk. How do I set my laptop to boot off of sda5?

Booting sda1 debian you "should" boot to a grub boot menu, and in this menu an option to boot ubuntu .
If you 'sudo update-grub' while booted in ubuntu then I would expect that ubuntu becomes the primary boot system.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by webmanoffesto on 2017-02-09
Using "Install Some Other Way" I can get to "Disks"
and I can Edit Partition /dev/sda2 Extended
And I can check off the box "Bootable" and I can make it "Linux (0x83)"
Is that is the right thing to do?

> **Bashing-om said:**
> 
sudo mkdir /mnt/looksee


```

tom@TomsAsusK55A:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=10240k,nr_inodes=214596,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=299524k,mode=755)
/dev/disk/by-uuid/32730290-3726-43d4-b7c0-0d0fe62946c8 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /run/shm type tmpfs (rw,nosuid,nodev,noexec,relatime,size=599040k)
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,nosuid,nodev,noexec,relatime)


```


```

tom@TomsAsusK55A:~$ sudo mkdir /mnt/looksee
[sudo] password for tom: 
tom@TomsAsusK55A:~$ sudo mount /dev/sda5 /mnt/looksee
tom@TomsAsusK55A:~$ ls -al /mnt/looksee
total 2332
[FONT=courier new]drwxr-xr-x  24 root root     4096 Dec 16 14:36 .
drwxr-xr-x   3 root root     4096 Feb  9 13:39 ..
drwxr-xr-x   2 root root     4096 Nov 22 15:16 bin
drwxr-xr-x   3 root root     4096 Dec  6 10:12 boot
drwxrwxr-x   2 root root     4096 May 21  2016 cdrom
-rw-------   1 root root 19529728 Dec 16 14:36 core
drwxr-xr-x   5 root root     4096 Apr 21  2016 dev
drwxr-xr-x 152 root root    12288 Dec 15 13:31 etc
drwxr-xr-x   2 root root     4096 May 21  2016 home
lrwxrwxrwx   1 root root       32 Dec  6 10:12 initrd.img -> boot/initrd.img-4.4.0-53-generic
lrwxrwxrwx   1 root root       32 Nov 30 08:34 initrd.img.old -> boot/initrd.img-4.4.0-51-generic
drwxr-xr-x  27 root root     4096 Oct 30 21:47 lib
drwxr-xr-x   2 root root     4096 Oct 30 21:47 lib64
drwx------   2 root root    16384 May 21  2016 lost+found
drwxrwxrwx   3 root root     4096 May 21  2016 media
drwxr-xr-x   2 root root     4096 Apr 21  2016 mnt
drwxr-xr-x   3 root root     4096 May 22  2016 opt
drwxr-xr-x   2 root root     4096 Apr 12  2016 proc
drwx------  11 root root     4096 Dec 16 14:36 root
drwxr-xr-x  11 root root     4096 Apr 21  2016 run
drwxr-xr-x   2 root root    12288 Oct 30 21:49 sbin
drwxr-xr-x   2 root root     4096 Apr 19  2016 snap
drwxr-xr-x   2 root root     4096 Apr 21  2016 srv
drwxr-xr-x   2 root root     4096 Feb  5  2016 sys
drwxrwxrwt   8 root root     4096 Dec 18 20:31 tmp
drwxr-xr-x  10 root root     4096 Apr 21  2016 usr
drwxr-xr-x  14 root root     4096 Apr 21  2016 var
lrwxrwxrwx   1 root root       29 Dec  6 10:12 vmlinuz -> boot/vmlinuz-4.4.0-53-generic
lrwxrwxrwx   1 root root       29 Nov 30 08:34 vmlinuz.old -> boot/vmlinuz-4.4.0-51-generic[/FONT]

tom@TomsAsusK55A:~$ ls -al /mnt/looksee/home
total 8
drwxr-xr-x  2 root root 4096 May 21  2016 .
drwxr-xr-x 24 root root 4096 Dec 16 14:36 .


```

---

### Post by oldfred on 2017-02-09
If you have two installs of Linux grub should offer to boot either one.
Normally the first in menu is default that is installed to MBR. And near bottom of menu is whereother installs boot should be in menu.

If you boot into Ubuntu you can reinstall its grub to MBR.

       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo parted -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

---

### Post by Bashing-om on 2017-02-09
webmanoffesto; Andddd ...

getting closer .
we now have a UUID that is booting for the root partition .
now we need to cross reference the UUID:
> 
/dev/disk/by-uuid/32730290-3726-43d4-b7c0-0d0fe62946c8 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)

to the device ID.
now show:
```

sudo blkid

```
and then we know the booted partition and can then know which operating system to replace.

Now comes the question :
> 
tom@TomsAsusK55A:~$ ls -al /mnt/looksee/home

why there is no home directory ??? Is the sda5 partition actually your /home ??
Presently does not compute.
So, show what the system is mounting from it's config file :
```

cat /etc/fstab

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by webmanoffesto on 2017-02-09
[FONT=courier new]tom@TomsAsusK55A:~$ sudo blkid
/dev/sda1: UUID="32730290-3726-43d4-b7c0-0d0fe62946c8" TYPE="ext4" 
/dev/sda5: UUID="7d9d5715-68cb-4560-b2da-0928d27338d5" TYPE="ext4" 
/dev/sda6: UUID="4241ce6d-a454-48ac-8e60-a6cba2023f05" TYPE="swap" 

tom@TomsAsusK55A:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6ba69c54-9f95-4685-9f0d-a98c9830cc64 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0




[/FONT]

---

### Post by Bashing-om on 2017-02-09
webmanoffesto; Ho Kay .

confirmed that you are booting from the sda1 partition at this time.
Now the question remains; What is sda5 ??
And also while here your swap UUID is invalid:
> 
UUID=6ba69c54-9f95-4685-9f0d-a98c9830cc64 none swap sw 0 0

that UUID per blkid should be:
" 4241ce6d-a454-48ac-8e60-a6cba2023f05 "
Fire up your favorite text editor and edit in the correct UUID for swap in the file /etc/fstab . ( SOP is make a backup of the current file prior to editing !)
Then when the file is saved terminal command:
```

mount -a

```
to make sure there is no typo . If a problem the system will advise . else if all good there will be no response.
-------------------------------

Now back to what sda5 is . No /home ?? no idea of the why . Did you at some point remove (delete) /home ?
> 
tom@TomsAsusK55A:~$ ls -al /mnt/looksee/home
total 8
drwxr-xr-x  2 root root 4096 May 21  2016 .
drwxr-xr-x 24 root root 4096 Dec 16 14:36 .
 is this the complete output ?
as what I expect to see is something similar to this:
> 
sysop@x1604:~$ ls -al /home
total 12
drwxr-xr-x  3 root  root  4096 Oct 16 22:47 .
drwxr-xr-x 25 root  root  4096 Feb  2 23:46 ..
drwxr-xr-x 28 sysop sysop 4096 Feb  9 13:22 sysop
sysop@x1604:~$ 

my output where it shows me (sysop) as having a home directory - where you do not .
and .............
> 
boot/vmlinuz-4.4.0-53-generic

indicates that you have not updated this install in some time.

Bottom line here is that you are booting sda1, now what do you want to do with sda5 ?

[INDENT][INDENT]make a plan and do it
[/INDENT][/INDENT]

---

### Post by webmanoffesto on 2017-02-09
[FONT=courier new]```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=32730290-3726-43d4-b7c0-0d0fe62946c8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=6ba69c54-9f95-4685-9f0d-a98c9830cc64 none            swap    sw              0       0
UUID=4241ce6d-a454-48ac-8e60-a6cba2023f05 none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```

tom@TomsAsusK55A:~$ sudo mount -a
sudo: /etc/sudoers is world writable
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

```
[/FONT]

> **Bashing-om said:**
> 
Now back to what sda5 is . No /home ?? no idea of the why . Did you at some point remove (delete) /home ?
 is this the complete output ?


Full text
```

tom@TomsAsusK55A:~$ ls -al /mnt/looksee/home
total 8
drwxr-xr-x  2 root root 4096 May 21  2016 .
drwxr-xr-x 24 root root 4096 Dec 16 14:36 ..
tom@TomsAsusK55A:~$ 

```

No, I did not intentionally delete Home.

> **Bashing-om said:**
> 
Now what do you want to do with sda5 ?

I think I can set that partition as the boot partition. Is that correct. And if I boot from that will I boot into Ubuntu?

---

### Post by Bashing-om on 2017-02-09
webmanoffestol Humm ...

Not a clue as to what you my have done to loose sudo .
The edit you make to /etc/fstab looks good to me. Did it save with the edits you made ?

What returns:
```

ls -al /etc/sudoers

```
Fixing sudo belongs in a new thread as it has nothing to do with the original issue here .

[INDENT][INDENT]ouch, strange things do happen
[/INDENT][/INDENT]

---

### Post by webmanoffesto on 2017-02-09
tom@TomsAsusK55A:~$ ls -al /etc/sudoers
-rwxrwxrwx 1 root root 669 May  3  2015 /etc/sudoers

I see that I boot into Debian GNU/Linux 7.11 (wheezy)
```

tom@TomsAsusK55A:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Debian
Description:    Debian GNU/Linux 7.11 (wheezy)
Release:    7.11
Codename:    wheezy

```

---

### Post by Bashing-om on 2017-02-09
webmanoffesto; Ouch !

A new thread on the sudo issue .
should be:
> 
sysop@x1604:~$ ls -al /etc/sudoers
-r--r----- 1 root root 755 Aug 17 08:20 /etc/sudoers
sysop@x1604:~$ 
Might should get this fixed as a 1st priority .

[INDENT][INDENT]yukkie
[/INDENT][/INDENT]

---

### Post by webmanoffesto on 2017-02-09
New thread at [https://ubuntuforums.org/showthread.php?t=2352130&p=13605317#post13605317](https://ubuntuforums.org/showthread.php?t=2352130&p=13605317#post13605317)

Sudo problem resolved. I think I want to boot off of sda5 now, which should put me into Ubuntu. Does that sound like the right thing to do? If so, how do I do that?

---

### Post by oldfred on 2017-02-09
Do you have that as a boot option currently from grub in sda1?
If not run this:
sudo update-grub

And if booted into install in sda5, see post #12.

---

### Post by webmanoffesto on 2017-02-09
Seems to have worked, wish me luck while I reboot.

```

tom@TomsAsusK55A:~$ sudo update-grub
sudo: /etc/sudoers.d is world writable
[sudo] password for tom: 
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.4-9-rtai-686-pae
Found initrd image: /boot/initrd.img-3.4-9-rtai-686-pae
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
done

```

No, that didn't work
tom@TomsAsusK55A:~$ sudo update-grub
sudo: /etc/sudoers.d is world writable

But on reboot I didn't have a boot into Ubuntu option.

My options were
Debian Gnu Linux
Debian Gnu Linux recovery mode
Memtest (multiple)

---

### Post by oldfred on 2017-02-09
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by webmanoffesto on 2017-02-10
> **oldfred said:**
> 
Post the link to the Create BootInfo summary report.


Here is the output of the BootInfo summary report
[http://paste.ubuntu.com/23966505/](http://paste.ubuntu.com/23966505/)

[COLOR=#666666]===================[/COLOR] 
Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sda1 into the MBRs of all disks [COLOR=#666666]([/COLOR]except USB without OS[COLOR=#666666])[/COLOR].
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s

[COLOR=#666666]===================[/COLOR] 
Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (1000GB) disk!


=================== 
User settings
The settings chosen by the user will not act on the boot.

---

### Post by oldfred on 2017-02-10
I am not sure your Ubuntu install will work.
You have set your Debian install as /home in Ubuntu. No idea what that will do, but expect booting Ubuntu may corrupt Debian. Or if you installed Debian after Ubuntu you may have erased some of /home in Ubuntu?

If somehow Ubuntu is working, you can use Boot-Repair's advanced mode to choose Ubuntu install in sda5 and install grub2 boot loader into MBR.

You show a lot of data in sda1. Is that well backed up?

With multiple installs better to keep system in smaller partition. I have multiple Ubuntu installs and use 25GB for each install including /home. But I have a large /mnt/data partition as I want same data in all installs, but not same configuration settings from /home.

---

### Post by webmanoffesto on 2017-02-10
Thanks. Using an Ubuntu Gnome 16 live disk I reformatted sda5 (to ext4) and installed Ubuntu Gnome to sda5. I marked the partition as bootable. It's working great.

---

### Post by Bashing-om on 2017-02-10
webmanoffesto; Great !

Pleased ya got it all worked out :)

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

