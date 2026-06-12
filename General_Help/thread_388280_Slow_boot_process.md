---
title: "Slow boot process"
date: 2007-03-19
forum: General Help
---

### Post by kwaanens on 2007-03-19
Running Edgy with all updates on an MSI 12" laptop. Boot time takes too long. 
I tried without usplash to see what the boot process stopped at, but that really didn't give me more clues. It hangs just after fsck /dev/hda3, and when it finishes it takes less than a second to get me to the login prompt.

Here's my /var/log/boot:
```
$ cat /var/log/boot
Mar 19 15:29:22 rcS:  * Reading files needed to boot...                  [ ok ] 
Mar 19 15:29:23 rcS:  * Setting preliminary keymap...                    [ ok ] 
Mar 19 15:29:24 rcS:  * Preparing restricted drivers...                  [ ok ] 
Mar 19 15:29:24 rcS:  * Starting basic networking...                     [ ok ] 
Mar 19 15:29:24 rcS:  * Starting kernel event manager...                 [ ok ] 
Mar 19 15:29:31 rcS:  * Loading hardware drivers...                      [ ok ] 
Mar 19 15:29:31 rcS:  * Loading manual drivers...                        [ ok ] 
Mar 19 15:29:31 rcS:  * Mounting local filesystems...                    [ ok ] 
Mar 19 15:29:31 rcS:  * Activating swapfile swap...                      [ ok ] 
Mar 19 15:30:38 rcS:  * Configuring network interfaces...                [ ok ] 
Mar 19 15:30:38 rcS:  * Setting sensors limits...                        [fail] 
Mar 19 15:30:38 rcS:  * Setting up console font and keymap...            [ ok ] 
Mar 19 15:30:39 rc2:  * Saving VESA state...                             [ ok ] 
Mar 19 15:30:39 rc2:  * Loading ACPI modules...                          [ ok ] 
Mar 19 15:30:39 rc2:  * Starting ACPI services...                        [ ok ] 
Mar 19 15:30:39 rc2:  * Starting system log...                           [ ok ] 
Mar 19 15:30:39 rc2:  * Starting kernel log...                           [ ok ] 
Mar 19 15:30:40 rc2:  * Starting GNOME Display Manager...                [ ok ] 
Mar 19 15:30:40 rc2:  * Starting Common Unix Printing System: cupsd      [ ok ] 
Mar 19 15:30:41 rc2:  * Starting HP Linux Printing and Imaging System    [ ok ] 
Mar 19 15:30:41 rc2:  * Starting system message bus dbus                 [ ok ] 
Mar 19 15:30:43 rc2:  * Starting Hardware abstraction layer hald         [ ok ] 
Mar 19 15:30:43 rc2:  * Starting DBUS aware dhcp client: dhcdbd          [ ok ] 
Mar 19 15:30:44 rc2:  * Starting NetworkManager daemon                   [ ok ] 
Mar 19 15:30:44 rc2:  * Starting NetworkManager dispatcher               [ ok ] 
Mar 19 15:30:44 rc2:  * Starting System Tools Backends system-tools-backe[ ok ]    
Mar 19 15:30:44 rc2: Starting MTA: exim4.
Mar 19 15:30:44 rc2:  * Starting disk temperature monitoring daemon hddte[ ok ]    
Mar 19 15:30:45 rc2: Starting powertweak: done
Mar 19 15:30:45 rc2: Starting sensor daemon: sensordError reading /proc or /sys; modules probably not loaded
Mar 19 15:30:45 rc2: .
Mar 19 15:30:45 rc2:  * Starting Bluetooth services                      [ ok ] 
Mar 19 15:30:45 rc2:  * Starting power management daemon powersaved      [ ok ] 
Mar 19 15:30:45 rc2:  * Starting anac(h)ronistic cron: anacron           [ ok ] 
Mar 19 15:30:45 rc2:  * Starting deferred execution scheduler atd        [ ok ] 
Mar 19 15:30:45 rc2:  * Starting periodic command scheduler...           [ ok ] 
Mar 19 15:30:45 rc2:  * Enabling additional executable binary formats bin[ ok ] port       
Mar 19 15:30:45 rc2:  * Checking battery state...                        [ ok ] 
Mar 19 15:30:45 rc2:  * Running local boot scripts (/etc/rc.local)       [ ok ]
```

The long hold looks to occur between "Activating swapfile swap..." and "Configuring network interfaces..."

I also don't like the line that says: "Mar 19 15:30:38 rcS:  * Setting sensors limits...                        [fail]" Is that something I should worry about?

- Ketil

---

### Post by gapplewagen on 2007-03-19
Could possibly be filesystem corruption.  Try booting to live cd and running fsck manually against your primary partition.

```

fsck -Va

```

V == verbosity
a == automatically repair

---

### Post by kwaanens on 2007-03-19
Will try this later, but it does sound weird. Wouldn't fsck give me something of a notice before it mounts the partition then? And this has been going on at least for several weeks, with at least 3-4 boots per day.

- Ketil

---

### Post by gapplewagen on 2007-03-19
You would think so.  I have a system that is having fs issues and in dmesg I get:

```

[17179578.824000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179578.824000] EXT3-fs: write access will be enabled during recovery.
[17179580.536000] EXT3-fs: recovery complete.
[17179580.540000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.156000] EXT3 FS on hda1, internal journal

```

but fsck fixed it.

What is the output of:

```

dmesg|grep fs

```

??

---

### Post by Death_Sargent on 2007-03-19
ok i would sujjest the fsck method only last i checked ubuntu does this automatically whenever a crash is detected 

If doing it manually does not work use gnome partion managerto check how much is in each volume. 

if you dont have then

> sudo apt-get install gparted

you can also infact should do this from the install disk that already has gparted (gnome partition manager)

Try reformating your swap partition (the red one)

If anything is in there it will be deleted and it will be brand new in a sense so the error will probubly go away

---

### Post by gapplewagen on 2007-03-19
> **Death_Sargent said:**
> ok i would sujjest the fsck method only last i checked ubuntu does this automatically whenever a crash is detected 



I thought this too... but the system I was having problems with stated that "recovery complete" but I was still having issues when mounting any other filesystems.  After a manual fsck the problem was resolved.

---

### Post by kwaanens on 2007-03-19
> **gapplewagen said:**
> 
What is the output of:

```

dmesg|grep fs

```

??

$ dmesg | grep fs
[17179573.060000] checking if image is initramfs... it is
[17179576.960000] usbcore: registered new driver usbfs
[17179577.748000] EXT3-fs: mounted filesystem with ordered data mode.
[17179589.376000] EXT3-fs: mounted filesystem with ordered data mode.

---

### Post by kwaanens on 2007-03-19
As I suspected, it returned no errors. However:

$ fsck -Va /dev/hda2
fsck 1.39 (29-May-2006)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/hda2

Any other thoughts?

I should say I keep getting an error when I boot without usplash telling me:
"[17179582.636000] sdhci:slot0: Unknown controller version (16). You may experience problems."

This does not show up in /var/log/messages, but in /var/log/syslog

However, I think this is the SD card reader, which incidentally worked out of the box.

- Ketil

---

### Post by gapplewagen on 2007-03-19
Is /dev/hda2 your root filesystem or swap space?  If it's swap, I would also suggest reformatting it.

---

### Post by kwaanens on 2007-03-19
Yes, it is swap. I started Gparted, "swapoffed" it and reformatted it while logged in Ubuntu, then "swapon". Got no errors, but still get: 
$ fsck -Va /dev/hda2
fsck 1.39 (29-May-2006)
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/hda2

But this has, I'm assuming, nothing to do with the swap partition, but the fact that I have no fsck.swap command:

$ fsck [double tab]
fsck           fsck.ext2      fsck.minix     fsck.nfs       fsck.vfat
fsck.cramfs    fsck.ext3      fsck.msdos     fsck.reiserfs

---

### Post by gapplewagen on 2007-03-20
After going through the man pages for fsck and fsck.ext3, I realized the options are quite different.

-V in fsck means to print version, not be verbose

The options for your root filesystem should be:

```

fsck.ext3 -pvf

```

-p replaces -a for automatically repairing errors.  -f forces it to scan the whole filesystem even if it's considered clean.  -v is now verbose instead of -V

Give it a shot.

---

### Post by kwaanens on 2007-03-20
Result:

/;

```
$ sudo fsck.ext3 -pvf /dev/hda1
/dev/hda1: recovering journal

  295797 inodes used (13%)
    4466 non-contiguous inodes (1.5%)
         # of inodes with ind/dind/tind blocks: 17052/157/0
 2265042 blocks used (52%)
       0 bad blocks
       0 large files

  250662 regular files
   20630 directories
     141 character device files
      43 block device files
       2 fifos
     370 links
   24309 symbolic links (22384 fast symbolic links)
       1 socket
--------
  296158 files
```

swap, og course fails in checking;

```
$ sudo fsck.ext3 -pvf /dev/hda2
fsck.ext3: Bad magic number in super-block while trying to open /dev/hda2
/dev/hda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

and, finally, my file archive:

```
$ sudo fsck.ext3 -pvf /dev/hda3
/dev/hda3: recovering journal

   63625 inodes used (0%)
     698 non-contiguous inodes (1.1%)
         # of inodes with ind/dind/tind blocks: 11300/4054/0
14699607 blocks used (75%)
       0 bad blocks
       0 large files

   57481 regular files
    6135 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
       0 symbolic links (0 fast symbolic links)
       0 sockets
--------
   63616 files
```

However, I see, when I run gparted, that none of the partitions have flags. Shouldn't they?

..Ketil

---

### Post by mcduck on 2007-03-20
> **kwaanens said:**
> 
```
$ sudo fsck.ext3 -pvf /dev/hda2
fsck.ext3: Bad magic number in super-block while trying to open /dev/hda2
/dev/hda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```

Well, it's supposed to be a swap partition so you can't run fsck on it :D

Anyway, could you post your /etc/fstab and output of 'sudo fdisk -l' here?

edit: the reason for error about fsck.swap is that such program doesn't even exist. running fsck checks what the file system is, and then tries to call right program to do the job. Running fsck, or fsck.ext3 on ext3 partition actually calls e2fsck to check the partition. There is no program to check swap as that would be rather useless ;)

---

### Post by kwaanens on 2007-03-20
```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f19f67ff-9be1-4f5a-af99-84fcdf6a41d5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=e2f015a1-7d2d-4124-aac2-26010ba1c354 /media/arkiv    ext3    defaults        0       2
# /dev/hda2
UUID=4e5b00f3-88d8-40e1-9824-a88abbc7d09d none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/sda1     /media/300      ext2    users,defaults      0       0
```


```
$ sudo fdisk -l
Password:

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2162    17366233+  83  Linux
/dev/hda2           11907       12161     2048287+  82  Linux swap / Solaris
/dev/hda3            2163       11906    78268680   83  Linux

Partition table entries are not in disk order
```

---

### Post by mcduck on 2007-03-20
Ok, you mentioned that you have reformatted the swap partition (dev/hda2). After doing that did you check it's new UUID number and change /etc/fstab to use the new UUID? First thing to do would be to either do that or replace the UUID with '/dev/hda2'

You can get UUID numbers for partitions by running 'ls -la /dev/disk/by-uuid'

Other than that, your fstab at least seems to be fine.

---

### Post by kwaanens on 2007-03-20
```
$ ls -la /dev/disk/by-uuid
totalt 0
drwxr-xr-x 2 root root 100 2007-03-20 22:14 .
drwxr-xr-x 5 root root 100 2007-03-20 22:12 ..
lrwxrwxrwx 1 root root  10 2007-03-20 22:14 639aedb3-ce95-4949-9bbe-675547209f87 -> ../../hda2
lrwxrwxrwx 1 root root  10 2007-03-20 22:12 e2f015a1-7d2d-4124-aac2-26010ba1c354 -> ../../hda3
lrwxrwxrwx 1 root root  10 2007-03-20 22:12 f19f67ff-9be1-4f5a-af99-84fcdf6a41d5 -> ../../hda1
```

I have to say, I don't understand this.

However:
My reformatting of swap was after this thread was started, just to say if it did something. 
I have not touched the partition table or any of the "active" lines in fstab at all. I'll try changing to /dev/hdax.

- Ketil

---

### Post by kwaanens on 2007-03-20
Update: fstab now changed slightly, which did nothing.

```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
## UUID=f19f67ff-9be1-4f5a-af99-84fcdf6a41d5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
/dev/hda3       /media/arkiv    ext3    defaults        0       2
## UUID=e2f015a1-7d2d-4124-aac2-26010ba1c354 /media/arkiv    ext3    defaults        0       2
# /dev/hda2
/dev/hda2       none            swap    sw              0       0
## UUID=4e5b00f3-88d8-40e1-9824-a88abbc7d09d none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/sda1     /media/300      ext2    users,defaults      0       0
```

Still a 1 minute hold during boot.

---

### Post by mcduck on 2007-03-20
That output is telling that the UUID for hda2 is now 639aedb3-ce95-4949-9bbe-675547209f87, not the 4e5b00f3-88d8-40e1-9824-a88abbc7d09d you had in your fstab. UUID number changes when you format a partition.

Anyway, I'm pretty sure your original problem is not caused by the swap partition but something else instead.

edit: to get a bit more detailed info during the boot process you could remove 'quiet' from your kernel line in /boot/Grub/menu.lst. That might help to find out what causes the slowdown.

---

### Post by kwaanens on 2007-03-20
OK. removing quiet and splash reveals that it hangs at "configuring network interfaces"

I think I may have found the problem, but I'm not capable of fixing it, it seems. I use network-manager to manage my network. I see that Ubuntu loves to automatically configure my ethernet card to use dhcp to connect to the net, but I don't want anything but network-manager to connect. I think this is the problem.

My wireless card is Intel PRO/Wireless 3945, the ethernet card is some Realtek stuff I think.

Allright, what happens is, if I access System > Administration > Network, the ethernet card is configured. If I deactivate it, it activates by itself with dhcp the next time I look at it.

Also, I'm used to that network-manager automatically chooses wired connection if available, but on this computer it doesn't.

Any clues?

---

### Post by mcduck on 2007-03-20
> **kwaanens said:**
> OK. removing quiet and splash reveals that it hangs at "configuring network interfaces"

I think I may have found the problem, but I'm not capable of fixing it, it seems. I use network-manager to manage my network. I see that Ubuntu loves to automatically configure my ethernet card to use dhcp to connect to the net, but I don't want anything but network-manager to connect. I think this is the problem.

My wireless card is Intel PRO/Wireless 3945, the ethernet card is some Realtek stuff I think.

Allright, what happens is, if I access System > Administration > Network, the ethernet card is configured. If I deactivate it, it activates by itself with dhcp the next time I look at it.

Also, I'm used to that network-manager automatically chooses wired connection if available, but on this computer it doesn't.

Any clues?Well, at least we now know where the problem is. But I have no idea what's causing it, I'm currently writing this on Asus A6JA laptop with Intel PRO/Wireless 3945ABG and Realtek wired ethernet, and everything is working fine for me.. (I'm using network manager also, it doesn't autoselect the wired network for me either but apart from that I have no problems)

If nothing else, at least you should be able to skip the network configuration during boot by pressing ctrl-c.

---

### Post by kwaanens on 2007-03-21
> **mcduck said:**
> If nothing else, at least you should be able to skip the network configuration during boot by pressing ctrl-c.

Actually, I thought that too. But that doesn't work :(

- Ketil

---

### Post by danzvash on 2007-03-22
Did you try commenting out all the interface lines in /etc/network/interfaces?

Think I remember that working for somebody else ....

Gonna try it myself when I get a chance 'cause I also have a very sloooow boot.

---

### Post by gapplewagen on 2007-03-22
> **danzvash said:**
> Did you try commenting out all the interface lines in /etc/network/interfaces?

Think I remember that working for somebody else ....

Gonna try it myself when I get a chance 'cause I also have a very sloooow boot.

I believe that the interfaces must be commented out if you want to use network manager to handle things for you.

---

### Post by kwaanens on 2007-03-22
That works beautifully! Thanks!

- Ketil

---

