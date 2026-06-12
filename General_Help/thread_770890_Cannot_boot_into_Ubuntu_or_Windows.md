---
title: "Cannot boot into Ubuntu or Windows"
date: 2008-04-27
forum: General Help
---

### Post by ashu9uf on 2008-04-27
Hi,

Earlier I had XP home and XP Pro on my desktop on 2 (out of 7) partitions. Then I installed Ubuntu on the XP Pro partition and everything was fine.

Then, in windows, I split one partition into two; and deleted one of the new partition so that I can claim it in linux later (to add space.) 

Shut down, restart, then no grub! So I installed grub using live CD. But now I see grub, but cannot boot into either ubuntu or XP.

As far as I understand, I changed the partition tables when I created the new partition while in windows; and MBR/Grub written with Ubuntu doesnt fix that. So, I used the testdisk utility while in live CD, to re-write the partition tables, but that didnt help. I also tried re-installing ubuntu without formatting the / partition but installation doesnt proceed further than that screen saying it NEEDS to format / to continue installation.

So, I believe my installations of Ubuntu and XP are fine, but I have my partition tables screwed up, hence MBR cannot direct to any OS and I am stuck.

Help! 

Thanks.

**UPDATE: Summary**

_What I did wrong:_ I split an existing partition into two using disk manager in Windows XP. This changed the partition tables, and the changes were not reflected in MBR with Grub on it.

_Remedy:_ Delete the partition in Windows; then boot in Ubuntu, and make two partitions out of the unallocated space and claim one for linux. Then, boot into Windows and claim the remaining unallocated space for a windows partition.

_Fixing the mess:_ Run testdisk and write partition tables, as well as generate boot sector for each partition as needed. I only wrote parition tables and that allowed me to boot to Ubuntu but not to Windows. Once I regenerated the boot sector for windows partition and other affected ones, everything worked like a charm.

_Remember:_
1. In order to access menu.1st file, you will need to mount the root partition when you booted using your live cd. 
2. mup.sys error while booting in safe mode in windows can also be casued due to bad boot sectors on each partition. (as it did in my case.)
3. Ubuntu rocks!

Hope it helps other noobies like me.

---

### Post by GCoffee on 2008-04-27
I'm not a expert in grub, but I think it might have something to do with installing ubuntu on the same partition as XP... I'm guessing your using hardy?

In the ubuntu setup (from live cd) were you asked which partiton/harddrive grub should be booted to?

Probably not the best advice ever given but i hope it helps.

---

### Post by ghost_ryder35 on 2008-04-27
Wow, did you have a seperate partion for "/home" if so you can go ahead and format "/" and then proceed with the install  Make sure you specify your "/home" directory in the partion page just do not format it.  If not you could try the UBCD4WIN and see if it can read your structure.  Or you could try to boot off a Windows XP cd and try like "fix boot" or "fixmbr".  WIsh I could be more help.

---

### Post by TeoBigusGeekus on 2008-04-27
Boot up with the live cd and try to locate your menu.lst file.
It is located in your ubuntu partition, in /boot/grub. Post us its contents.
Also, post us the output of
```
sudo fdisk -l
```

---

### Post by ashu9uf on 2008-04-27
I did not make a /home, and I really dont want to reinstall all over again, have already spent a month adding things to it.

I have 7.10, and both OS booted/worked fine until I split a windows FAT32 into two, and deleted one, and rebooted.

---

### Post by ashu9uf on 2008-04-27
fdisk and menu.1st in post below.

---

### Post by ghost_ryder35 on 2008-04-27
can you boot into windows now?  And as long as you do not format "/home" everything will still be where it was after the reinstall of Ubuntu

---

### Post by ashu9uf on 2008-04-27
Err... I messed further.

I tried to 'fixmbr' using windows recovery console. There was a warning about changing tables, and going by other people's postings (elsewhere) I went ahead.


ok, here are the files (attached.)
(I panicked and forgot to sudo fdisk)


No, after fixmbr I cannot logon to anything. Operating system not found.

> **ghost_ryder35 said:**
> can you boot into windows now?  And as long as you do not format "/home" everything will still be where it was after the reinstall of Ubuntu

Are you suggesting that any program I compile/make/install will be there in /home even after I reinstall fresh version in / partition? I thought it was like windows, where /home is just a data partition.

---

### Post by TeoBigusGeekus on 2008-04-27
Sorry, can't make out a single thing from the text files.
Would you be kind enough to post them as they are (no word wrapping and stuff) directly into the forum?

---

### Post by ghost_ryder35 on 2008-04-27
are you running the live cd? Your boot menu is trying to boot windows from the wrong drive... trying to boot from sda2
```
[SIZE=2]title Ubuntu 7.10, kernel 2.6.22-14-generic[/SIZE]
[SIZE=2]root (hd0,3)[/SIZE]
[SIZE=2]kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=02519466-7e4c-4f14-b918-c07c80498971[/SIZE]
[SIZE=2]initrd /boot/initrd.img-2.6.22-14-generic[/SIZE]
 
[SIZE=2]title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)[/SIZE]
[SIZE=2]root (hd0,3)[/SIZE]
[SIZE=2]kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=02519466-7e4c-4f14-b918-c07c80498971 ro single[/SIZE]
[SIZE=2]initrd /boot/initrd.img-2.6.22-14-generic[/SIZE]
[SIZE=2]title Ubuntu 7.10, memtest86+[/SIZE]
[SIZE=2]root (hd0,3)[/SIZE]
[SIZE=2]kernel /boot/memtest86+.bin[/SIZE]
 
[SIZE=2]### END DEBIAN AUTOMAGIC KERNELS LIST[/SIZE]
[SIZE=2]# This entry automatically added by the Debian installer for a non-linux OS[/SIZE]
[SIZE=2]# on /dev/**sda2**[/SIZE]
[SIZE=2]title Windows NT/2000/XP (loader)[/SIZE]
[SIZE=2]root (hd0,1)[/SIZE]
[SIZE=2]savedefault[/SIZE]
[SIZE=2]makeactive[/SIZE]

```
 
 
```

[SIZE=2]Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c
Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 * 7 978 7807590 83 Linux
/dev/sda3 979 3530 20498940 c W95 FAT32 (LBA)
/dev/sda4 3531 19453 127901497+ f W95 Ext'd (LBA)
/dev/sda5 3531 3791 2096419+ 82 Linux swap / Solaris
/dev/sda6 3792 4444 5245191 b W95 FAT32
/dev/sda7 4445 7055 20972826 7 HPFS/NTFS
/dev/sda8 7056 10971 31455238+ c W95 FAT32 (LBA)
/dev/sda9 10972 19452 68123601 7 HPFS/NTFS
Disk /dev/sdb: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 246 1974240 6 FAT16
Partition 1 has different physical/logical endings:
phys=(244, 254, 63) logical=(245, 200, 18)
[/SIZE]
```
According to that your sda2 is a Linux partiton

---

### Post by ashu9uf on 2008-04-27
Sorry about the formatting, didnt realize there wasnt any! here they are...

ahaan, I think hd0,* is wrong everywhere; can you suggest me the right values? sda2 is linux root, and sda3 is the windows xp.

**_Fdisk:_**


Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7         978     7807590   83  Linux
/dev/sda3             979        3530    20498940    c  W95 FAT32 (LBA)
/dev/sda4            3531       19453   127901497+   f  W95 Ext'd (LBA)
/dev/sda5            3531        3791     2096419+  82  Linux swap / Solaris
/dev/sda6            3792        4444     5245191    b  W95 FAT32
/dev/sda7            4445        7055    20972826    7  HPFS/NTFS
/dev/sda8            7056       10971    31455238+   c  W95 FAT32 (LBA)
/dev/sda9           10972       19452    68123601    7  HPFS/NTFS

Disk /dev/sdb: 2021 MB, 2021654016 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         246     1974240    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 200, 18)


_**Menu.1st**_

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

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

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
# kopt=root=UUID=02519466-7e4c-4f14-b918-c07c80498971 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02519466-7e4c-4f14-b918-c07c80498971 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=02519466-7e4c-4f14-b918-c07c80498971 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by ghost_ryder35 on 2008-04-27
what sda* is windows installed on?

---

### Post by ashu9uf on 2008-04-27
ahaan, I think hd0,* is wrong everywhere; can you suggest me the right values? sda2 is linux root, and sda3 is the windows xp.

---

### Post by TeoBigusGeekus on 2008-04-27
Linux is trying to boot from 

root (hd0,3)

that's your first hd, 4rth partition. According to your fdisk that is

/dev/sda4 3531 19453 127901497+ f W95 Ext'd (LBA)

completely irrelevant!!!

Also, windows is trying to boot from

root (hd0,1)

that's your first hd, 2rth partition. That is

/dev/sda2 * 7 978 7807590 83 Linux

which is of course your linux partition.

Change your menu.lst so that the linux entries boot on (hd0,1)
and windows on (hd0,6).

---

### Post by ghost_ryder35 on 2008-04-27
yea, what he said, so confused, so many partions, LOL

---

### Post by doorknob60 on 2008-04-27
I'm guessing here, but try changing your menu.lst where it says this: root (hd0,3) in Ubuntu, change them to this: root (hd0,1). Not positive it will fix it but it's worth a shot. EDIT: Looks like I'm too late... *looks up 2 posts*

---

### Post by ashu9uf on 2008-04-27
Fixed the entries in menu.1st and I can log on to Ubuntu. :) Thanks a lot guys.

But, not into Windows. I can see the windows loader (with two options), and when I choose my XP home, it is missing some file.

Should I fix the windows installation, then reinstall grub?

---

### Post by TeoBigusGeekus on 2008-04-27
If windows is in sd3 then you should change the grub entry for windows to (hd0,2). Sorry, I didn't notice earlier - thought the ntfs partition was window$....

---

### Post by ashu9uf on 2008-04-27
> **TeoBigusGeekus said:**
> If windows is in sd3 then you should change the grub entry for windows to (hd0,2). Sorry, I didn't notice earlier - thought the ntfs partition was window$....

I actually did that only.

---

### Post by TeoBigusGeekus on 2008-04-27
Are you sure sd3 is your winxp partition? It's a fat32 one.
What about sd7 or sd9?

---

### Post by ashu9uf on 2008-04-27
Did I mention that I had tried recovering this windows partition? And trying to install fresh xp in sd7?  Anyway, I think this makes it ineligible for ubuntu forums. 

Ubuntu is working now, and I am fine for the time being!

---

### Post by TeoBigusGeekus on 2008-04-27
If windows is in sd7 then you should change the grub entry for windows to (hd0,6). 

Make up your mind mate...:)

---

### Post by ashu9uf on 2008-05-02
**UPDATE: Summary**

_What I did wrong:_ I split an existing partition into two using disk manager in Windows XP. This changed the partition tables, and the changes were not reflected in MBR with Grub on it.

_Remedy:_ Delete the partition in Windows; then boot in Ubuntu, and make two partitions out of the unallocated space and claim one for linux. Then, boot into Windows and claim the remaining unallocated space for a windows partition.

_Fixing the mess:_ Run testdisk and write partition tables, as well as generate boot sector for each partition as needed. I only wrote parition tables and that allowed me to boot to Ubuntu but not to Windows. Once I regenerated the boot sector for windows partition and other affected ones, everything worked like a charm.

_Remember:_
1. In order to access menu.1st file, you will need to mount the root partition when you booted using your live cd. 
2. mup.sys error while booting in safe mode in windows can also be casued due to bad boot sectors on each partition. (as it did in my case.)
3. Ubuntu rocks!

Hope it helps other noobies like me.

---

