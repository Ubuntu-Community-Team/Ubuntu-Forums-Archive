---
title: "Mounting an encrypted disk from old computer"
date: 2015-11-16
forum: General Help
---

### Post by rimez on 2015-11-16
[FONT=verdana]Some time ago my old PC (with Ubuntu 14.04) died on me so bought a new one. The HDD on the old one was not doing so well (but still usable) so I just went ahead and used the new HDD with a clean install (again, 14.04).

[/FONT]
[FONT=verdana]Unfortunately, I just cannot figure out how to read the external disk. I thought it would be as simple as plugging it into the usb, enter the passphrase when prompted and then copy everything I needed. Nope. Doesn't work that way.

[/FONT]
[FONT=verdana]As you can see in the screenshot, everything mounts, I just have no access to the data :([/FONT]
[FONT=verdana][http://i.imgur.com/d7ngy5M.png](http://i.imgur.com/d7ngy5M.png)[/FONT]
[FONT=verdana]
Can someone walk a noob through mounting an (previously) encrypted external drive (using a USB adapter) on Ubuntu 14.04. Please. :)

[/FONT]
[FONT=verdana]I remember there being a post somewhere here or on reddit related to this topic but cannot find it. :( [/FONT]

---

### Post by zeron00 on 2015-11-16
You have to use cryptsetup to open the disk and after that you can mount the encrypted volumes where you want them.
The format of the command is:
```

sudo cryptsetup -v luksOpen /dev/sdXY <some-name>

```
Replace <some-name> with a name of your choice. X and Y in here are the disk name and partition number. For example, on my system I would do write:
```

sudo cryptsetup -v luksOpen /dev/sdb3 sdb3_crypt

```
Your setup will be different, of course. You can find out what the disk and the partition number are by using fdisk or lsblk command:
```

sudo fdisk -l

```
or
```

sudo lsblk

```

If you have lvm over luks you may have to activate your logical volumes. You can do it with this command:
```

sudo vgchange -ay

```
After you've opened the partition with cryptsetup you can mount it in  the directory of your choice and copy whatever you want from there. How you do it depends on whether you have a plain luks or lvm over luks. In the first case you do as usual:
```

sudo mkdir /mnt/olddisk
sudo mount /dev/mapper/sdb3_crypt /mnt/olddisk

```
(Replace "sdb3_crypt" with the right name -- the one used when you opened it. And you replace "sdXY" with whatever your disk is.)
But if you have lvm over luks you will need to mount logical volumes, not physical. Do this command:
```

sudo lvdisplay

```
This will show you all your logical volumes. Find the one you want to mount -- take the "LV Path" as the path to the partition. If, for example, it says "/dev/vgSys/lvroot" you can mount it in this way:
```

sudo mkdir /mnt/olddisk
sudo mount /dev/vgSys/lvroot /mnt/olddisk

```
Now you can copy your old data to your new system.
When you're done you can unmount the device and close the luks partition:
```

sudo umount /mnt/olddisk
sudo cryptsetup luksClose /dev/mapper/sdb3_crypt

```
Done! Now you can unplug you old HD.

---

### Post by rimez on 2015-11-16
Thanks so much for your help.

My issue is with this (and I see the problem)
> [COLOR=#000000][FONT=Ubuntu Mono]sudo mount /dev/vgSys/lvroot /mnt/olddisk[/FONT][/COLOR]

Since my "new" HDD already has the same LV PATH as the old HDD (both we formatted during a fresh install of Ubuntu using the standard method), when I try to mount it to /mnt/olddisk it mounts the new disk (which is already mounted as root) to /mnt/olddisk :( 

I don't want to change the LV name of my new disk as I assume it'll break my system when I reboot.  Any idea? Can I change the LV PATH of the old disk?

============
> sudo lsblk
NAME                           MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                              8:0    0 232.9G  0 disk  
&#9500;&#9472;sda1                           8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                           8:2    0     1K  0 part  
&#9492;&#9472;sda5                           8:5    0 232.7G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)          252:0    0 232.7G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root (dm-1)   252:1    0 224.8G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1 (dm-2) 252:2    0   7.9G  0 lvm   [SWAP]
sdb                              8:16   0 465.8G  0 disk  
&#9500;&#9472;sdb1                           8:17   0   512M  0 part  
&#9500;&#9472;sdb2                           8:18   0   244M  0 part  /media/USER/f10f6fbf-894c-4891-9d78-324bc831a285
&#9492;&#9472;sdb3                           8:19   0   465G  0 part  
  &#9492;&#9472;ARCHIVE (dm-3)             252:3    0   465G  0 crypt 




> sudo lvdisplay 
 --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root
  LV Name                root
  VG Name                ubuntu-vg
  LV UUID                EY0aYh-s7sT-0Tew-sp4g-c5xN-WNCB-adQpqR
  LV Write Access        read/write
  LV Creation host, time ubuntu, 2015-05-02 08:01:38 +0200
  LV Status              NOT available
  LV Size                457.28 GiB
  Current LE             117064
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto




---

### Post by zeron00 on 2015-11-16
> **rimez said:**
> Thanks so much for your help.

My issue is with this (and I see the problem)


Since my "new" HDD already has the same LV PATH as the old HDD (both we formatted during a fresh install of Ubuntu using the standard method), when I try to mount it to /mnt/olddisk it mounts the new disk (which is already mounted as root) to /mnt/olddisk :( 

I don't want to change the LV name of my new disk as I assume it'll break my system when I reboot.  Any idea? Can I change the LV PATH of the old disk?

============

Hmm... There is a bunch of commands in lvm for manipulation of volumes and volume groups. Specifically, there is a command "lvrename", but I've never used it and so am unsure of how to do it safely. If you're gonna use it take care not to rename your new volumes in your new system. :eek: Check out documentation for this and other related commands: [http://linux.die.net/man/8/lvrename](http://linux.die.net/man/8/lvrename)
The safest way that I can think of is not very elegant. The thing is every file system in linux has a unique identifier (UUID -- a long string of hexadecimal characters) and so every block device can be referred to by its uuid. But I don't know if the mount command can use these identifiers for mounting (you can try it). But ubuntu uses UUID's in fstab to mount your root and other filesystems. So, what you can do is **[COLOR=#800080]temporarily [/COLOR]**edit fstab file, and after you're done copying your data **[COLOR=#4b0082]remove any changes[/COLOR]** you made to it. If you forget to undo the changes to fstab then linux will complain at the next boot about volumes being unavailable or some such thing.
Append this line at the end of /etc/fstab (you need to be root):

```
UUID=<your-volumes-uuid-number>   /mnt/[COLOR=#000000][FONT=Ubuntu Mono]olddisk[/FONT][/COLOR]   ext4  defaults   0 0
```

Replace <your-volumes-uuid-number> with the real UUID of your old volume. To find the uuid you can type "blkid" in the terminal.
When you've edited fstab type this command:
```
sudo mount -a
```
and you should have your old volume at /mnt/olddisk/
Do what you need, unmount (sudo umount /mnt/olddisk), put fstab back the way it was, close luks partition of the old disk and you're done!
As I said, this is an utterly inelegant solution, but, in my mind, it's safer than messing around with vgchange or lvrename, particularly when your old volumes and your new vo&#314;umes have the same names.

---

### Post by sandyd on 2015-11-16
For using vgrename, see below

Do this in a LiveCD, with new HDD unplugged. You can also use vgdisplay to get the two volume groups, determine which one is the new disk's vg, and get the "VG UUID". Then, you can just use the UUID instead of the "old vg" below.

Use cryptsetup to unlock LUKS before running the commands.

The syntax is
```

sudo vgrename *oldvg* *newvg*

```

In this case, do
```

sudo vgrename ubuntu-vg ubuntuold-vg
```

Boot back up into Ubuntu on the new HDD, and continue with the instructions provided above.

Please make sure you have backups/etc before performing any operations on a disk.

---

### Post by zeron00 on 2015-11-16
Yes, rimez, follow the advice from sandyd -- doing it from the LiveCD is a lot safer than from within your new system.

---

### Post by rimez on 2015-11-17
Thanks everyone for helping me out with this.  

So what I did today was, as suggested, 
1. removed the HDD from my computer
2. Booted the computer with a live USB (I don't have a CD/DVD drive) 
3. Plugged in the drive via USB... and then BAM
4. Entered my password for the external drive
5. Browsed the drive for the files I was looking for

That's it. 

So basically the problem is that whenever you install Ubuntu on a computer, if you select the default options for formatting and encryption, it'll use the same VG name.  I've never fiddled with the custom install. Does anyone know if it's possible to assign your own VG name during install?

---

