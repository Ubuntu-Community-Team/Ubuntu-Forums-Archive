---
title: "[SOLVED] Can't boot! Kernel panic"
date: 2007-11-24
forum: General Help
---

### Post by jken146 on 2007-11-24
In a normal boot I get nowhere at all after GRUB; in recovery mode this is what I get:

```
VFS: Cannot open root device "UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf" or unknown block(0,0)

Please append a correct "root=" boot option; here are the available partitions:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```


I had a look with a liveCD and /boot/grub/menu.lst seems to have the correct partition for my /, namely (hd3,2) (where / is located on sda2 and there are also hda, hdc and hdd).

I am rather lost atm!

---

### Post by jken146 on 2007-11-24
bump

---

### Post by jken146 on 2007-11-24
bump

---

### Post by jken146 on 2007-11-25
bump

---

### Post by Linteg on 2007-11-25
Either there is something wrong with the UUID (shouldn't be, especially if you have booted before) or your filesystem, try running some filesystem checks from the live-cd environment.
```
fsck.yourfilesystem /dev/sda2
```
For example, with the default file system (ext3) you should run:
```
fsck.ext3 /dev/sda2
```

---

### Post by bingoUV on 2007-11-25
> **jken146 said:**
> In a normal boot I get nowhere at all after GRUB; in recovery mode this is what I get:

```
VFS: Cannot open root device "UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf" or unknown block(0,0)

Please append a correct "root=" boot option; here are the available partitions:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```I had a look with a liveCD and /boot/grub/menu.lst seems to have the correct partition for my /, namely (hd3,2) (where / is located on sda2 and there are also hda, hdc and hdd).

I am rather lost atm!

Even if sda is hd3 (which can be verified from /boot/grub/device.map), hd3,2 is not sda2, it is sda3. For sda2, you should write hd3,1. 

Then there is the chance of wrong UUID. Verify the UUID of /dev/sda2 by 
```

ls -l /dev/disk/by-uuid/

```

---

### Post by jken146 on 2007-11-25
Thanks for your replies.

Turns out I should have said sda3.  Thanks bingoUV.

The UUID is correct, and sda is hd3.

fsck.ext3 /dev/sda3 yields ```
ubuntu@ubuntu:~$ sudo fsck.ext3 /dev/sda3
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda3 has been mounted 26 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda3: 126557/1310720 files (0.7% non-contiguous), 1096176/2620595 blocks

``` or if it has been mounted fewer than 30 times since last check, ```
/dev/sda3: clean, 126557/1310720 files, 1096176/2620595 blocks

```
No errors as far as I can see.

Any more suggestions anyone?

---

### Post by confused57 on 2007-11-25
First you might try, highlighting your Ubuntu entry in the grub boot menu, press "e", then highlight the line with root, press "e" again, change root from (hd3,2) to (hd2,2), press "enter", then "b" to boot...if (hd2,2) doesn't work, then try (hd1,2).  If your UUID is correct in your menu.lst, it's the only thing I can think of that you might try ATM.

Edited, I see you've already checked your device.map.

---

### Post by jken146 on 2007-11-25
Would reinstalling GRUB help?

---

### Post by Linteg on 2007-11-25
> **jken146 said:**
> Would reinstalling GRUB help?
Not very likely, grub does what grub should, that is, loads the kernel and the initramfs. The kernel panics because its root=... parameter is wrong, or it just can't read off the disk (trouble with modules in the initramfs, or disk problem). If grub had been trying to load the kernel from the wrong partition or otherwise failed, the kernel wouldn't have loaded and there wouldn't have been any kernel panic.
It would be nice if you attach your menu.lst and just to be on the safe side, make sure the partition mounts when you are using the live cd (can't really see why it shouldn't though)

---

### Post by jken146 on 2007-11-25
The partition does mount with the liveCD.  I will attach menu.lst when I get back to my usual comp.

---

### Post by jken146 on 2007-11-26
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd3,2)/boot/grub/splashimages/tuxos.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
password --md5 $1$HbqGF$o/Nlj4yNtKwWxiaH/DleH/
#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd3,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=true

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=792

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=true

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.22-14-generic
root		(hd3,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu, kernel 2.6.22-14-generic (recovery mode)
lock
root		(hd3,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu, memtest86+
root		(hd3,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by jken146 on 2007-11-26
I followed the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=620860") and it made no difference.

Here's me device.map: ```
(hd0)	/dev/hda
(hd1)	/dev/hdc
(hd2)	/dev/hdd
(hd3)	/dev/sda
```

---

### Post by heatblazer on 2007-11-26
Ugly error.I had the same on 5.12... Wasn`t able to fix that...Reinstalled it .. :S

---

### Post by jken146 on 2007-11-26
Thing is, I'd really rather not reinstall if I can help it.  I had everything going just as I liked it.  I hope I can avoid the frustration of having to reinstall.

---

### Post by athomson on 2007-11-27
Hi,

Hmm, this is not too bad, a few disks, but not too bad. 

First thing is the error message, it gives you a good hint at where the problem is:

```
VFS: Cannot open root device "UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf" or unknown [COLOR="Red"]block(0,0)[/COLOR]
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

See this [http://ubuntuforums.org/showthread.php?t=620860]("http://ubuntuforums.org/showthread.php?t=620860") for details on how grub works and how the boot process starts.  In your case, grub is working great. the problem is the initrd.img has the wrong path.

I highlighted the problem indicator in [COLOR="Red"]red,[/COLOR] this the disk and partition that the kernel is trying to load from.  In your case the kernel is told to load [in grub terms] from disk 0, partition 0.

Error Message
```

Grub: hd(0,0)
Real:  /dev/hda1

```

From your menu.lst file, you really want to be booting from is disk 3, partition 3. 

What you really want
```

Grub: hd(3,2)
Real: /dev/sda3

```

Remember there are two locations for the partition that is to be used, one is in the Grub menu, and the other one is in the initrd.img file.  From your posting the Grub menu is correct, and from the error message, the initrd.img file is wrong.

Those instructions on the post listed above should work for you. I can only think of two reasons that they did not: 1) wrong Grub menu setting, or 2) the '/boot' partition is really on it's partition. I think that the second reason is the case here.

For now I will assume that the '/boot' partition is likely on it's own, and you most likely installed it as the first partition on /dev/sda. I will assume that the next partition was swap and that root is the third one.

```

Device       Name    Grub
/dev/sda1   /boot    (hd3,0)
/dev/sda2   swap    
/dev/sda3   /         (hd3,2)

```

Since the details are in the other post, I am just going to show the commands here:

Boot from the Ubuntu Install Cdrom and open a terminal:
```
Applications->Accessories->Terminal
```

Become root:
```
sudo -i
```

Create a temporary mount point
```
mkdir /mnt/work
```

Mount your root partition
```
mount /dev/sda3 /mnt/work 
```

Mount your boot partition
```
mount /dev/sda1 /mnt/work/boot
```

Set up the work environment
```
mount -o bind /dev /mnt/work/dev
mount -o bind /proc /mnt/work/proc
cp /proc/mounts /mnt/work/etc/mtab
```

Change root to the mount point
```
chroot /mnt/work/ /bin/bash
```

Update the mkinitrd image
```
update-initramfs -c -k 2.6.22-14-generic
```

Exit the change root environment
```
exit
```

Un-mount the two partitions
```
umount /mnt/work/boot
umount /mnt/work
```

Reboot

If this fails, reboot with the cdrom, open a terminal, become root, mount the work partition and get the fstab.

```
cat /mnt/work/etc/fstab
```

Post it here

Andy

---

### Post by athomson on 2007-11-27
Hi,

In the previous message I meant disk 4 which is really hd(3) in Grub terms. I was not paying attention to real vs grub.  In any case the actually commands are correct.  

Andy

---

### Post by jken146 on 2007-11-27
Andy,

Thanks very much for your post.  In my case, /boot is located within the / partition (sda is partitioned with / (sda3) at the beginning of the disk, swap (sda1) at the end of the disk and /home (sda2) in the middle).

I have followed the commands as given exactly several times.  I get no error messages and initrd.img seems to be updated fine.

Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=bfaf3ff7-2841-46f9-8a8e-ce0337a85ae7 /home           ext3    defaults        0       2
# /dev/hda1
UUID=BC2CC7262CC6DA92 /mnt/xp     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda2
UUID=c0469cb7-8c94-4f76-9aad-5fcb9ea01124 /mnt/storage     ext3    defaults        0       2
# /dev/hda5
UUID=3751-CFD1  /mnt/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdc2
UUID=23dd5f79-ad5e-4015-9717-c36d15e24747 /mnt/storage2     ext3    defaults        0       2
# /dev/hdd2
UUID=87802506-dff0-4c2b-9e33-7c624ce19603 /mnt/storage3     ext3    defaults        0       2
# /dev/sda1
UUID=da3b18b6-f6cd-48aa-9fe7-c11ea2a5481a none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by athomson on 2007-11-27
Hi,

Linteg might have been on to something with the modules.  Do some checks before we go there.

As far as I can tell the Grub and it's related files are correct.   I am not so sure about the initrd.img file though, as it still points to hd(0,0), which is the Windows disk/partition. It would be useful to get some more information about what is going on with the boot.

Reboot  and stop at the Grub menu by hitting the Escape key.

Using the Arrow keys move to the first line, which is the default boot, or it should be.

```
 "Ubuntu, kernel 2.6.22-14-generic"
```

Press the "E" key to edit this entry.

Use the  arrow keys to move down to the line that looks like this [kernel line]:

```
kernel	/boot/vmlinuz-2.6.22-14-generic root=UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf ro quiet splash vga=792
```

Press the "E" key to edit this line.

You will make four changes to line, you will remove the vga=792, remove the splash, remove the quiet and change root=/dev/sda3.  It's easier to just backspace until you get to the root=, then type in 'root=/dev/sda3 ro'.  Make sure you add the 'ro' [read-only] flag or your kernel will not boot for sure.

```
kernel	/boot/vmlinuz-2.6.22-14-generic root=/dev/sda3 ro
```

Once you have made those changes, hit the 'B' key to boot.

You should see a lot more information on the screen now.  Watch for errors, and see what the kernel panic line has in it.  It should be looking for root at (3,2). If not then it indicates that the initrd.img was not updated correctly. 

 If the system boots, then there are two potential issues, the vga=792 is interfering with the boot process [not suppose to, but I have seen it happen], or the UUID is not correct or not being picked up correctly.  You can eliminate the latter one by rebooting, re-edit the kernel line,  remove vga=792, splash, and the quiet parts, leave the root="uuid" alone.  Then press 'B" to boot. If the boot hangs, then it's the UUID, if the boot works, then it's the vga=792.  

Before posting any further information about actions, modules, I'll wait to see what your results are.  

Andy

---

### Post by jken146 on 2007-11-28
It was the vga=792.  So glad I'm sorted now.  Thanks for your help.

---

### Post by gubemton on 2007-11-28
athomson

I did exactly what you said and it did not work for me, so I guess it is the UUID?

What should I do?

---

### Post by athomson on 2007-11-28
Gubemton,

Are you seeing a kernel panic? Or is it just not booting?  It would be useful if you could post the /boot/grub/menu.lst file.  You can boot from the cdrom to get it.

Open a terminal

Applications->Accessories->Terminal

Become root

```
sudo -i
```

Get a listing of partitions and drives

```
fdisk -l 
```

Create a mount point

```
mkdir /mnt/work
```

Mount your root partition. I am using /dev/hda2 in this example, you will need to change it to match yours.

```
mount /dev/hda2 /mnt/work
```

Mount the boot partition

```
mount /dev/hda1 /mnt/work/boot
```

Now you have access to the /boot/grub directory, it will be here

```
/mnt/work/boot/grub
```

Depending on how your network is setup, you should be able to open a browser to this forum and the cut-and-paste the menu.lst [or attach it] to a message.  If not save it to a usb drive/stick or floppy so you have access to it.

If you can, grab the kernel panic message or at least note what the very end of the message has for the device it is trying to boot from.  The will be something like this:

```
Cannot open root device "UUID=3af3fe5f-5650-4d30-8a49-930079c36cdf" or unknown block[COLOR="Red"](0,0)[/COLOR]
```

---

Andy

---

### Post by athomson on 2007-11-28
Hi,

Forgot one more piece:

Get the uuid's

From the terminal session

```
 ls -l /dev/disk/by-uuid
```

Andy

---

