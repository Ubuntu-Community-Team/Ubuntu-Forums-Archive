---
title: "Quick question regarding"
date: 2008-06-25
forum: General Help
---

### Post by ybd on 2008-06-25
After using GParted to move some partitions around I, unsurprisingly, got Grub Error 17 on boot.

I'm using the LiveCD to edit menu.lst but I'm having a little problem. I just don't know where to tell Grub to load Ubuntu from - I have one hard drive, so to put it in a really silly but understandable terms, I need to find X in (0,X). I attached a pic of my current GParted screen... and here's my menu.lst:

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
timeout		4

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
# kopt=root=UUID=49ce7746-9e55-4331-96bc-1616845551b7 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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
# defoptions=quiet splash irqpoll all_generic_ide

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

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=49ce7746-9e55-4331-96bc-1616845551b7 ro quiet splash irqpoll all_generic_ide
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=49ce7746-9e55-4331-96bc-1616845551b7 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1 
```

Originally (before messing with GParted) menu.lst pointed to (0,8), and now I tried (0,5). Both don't work, so that should help a little, heh.
Thanks for the help.

---

### Post by Elfy on 2008-06-25
can you either post the pic or run this from a terminal

```
sudo fdisk -l
```

---

### Post by ybd on 2008-06-25
I'm assuming you replied before I got the attachment working

but here's what I get from flist -l

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sda2           16709       25055    67047277+   7  HPFS/NTFS
/dev/sda3           25056       30401    42941745    5  Extended
/dev/sda5           30290       30401      899608+  82  Linux swap / Solaris
/dev/sda6           25056       25103      385497   83  Linux
/dev/sda7           30169       30289      971901   82  Linux swap / Solaris
/dev/sda8           25104       30054    39768876   83  Linux
/dev/sda9           30055       30168      915673+  82  Linux swap / Solaris

```

---

### Post by drs305 on 2008-06-25
From you picture it looks like (0,7) for sda8 would be the answer but your gparted image shows 3 swap partitions.

Can you post your fstab?
```

cat /etc/fstab

```

---

### Post by ybd on 2008-06-25
```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

(0,7) didn't work, so i'm probably doing something wrong.

---

### Post by drs305 on 2008-06-25
This is the fstab for the livecd. Your real/normal fstab is probably on sda8, so from the livecd you have to mount that partition to look at it.

See if this gives you your fstab:

```

sudo mkdir /temp1
sudo mount /dev/sda8 /temp1
cat /temp1/etc/fstab

```

---

### Post by ybd on 2008-06-25
Damn it, didn't notice that for some reason my HD wasn't recognized on that boot of the LiveCD. Sorry.

Here's the "real" fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=49ce7746-9e55-4331-96bc-1616845551b7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=2007de55-53cf-42aa-9b79-23a2daed9257 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#Added by diskmounter utility
/dev/sda2 /media/sda2 ntfs ro,user,fmask=0111,dmask=0000 0 0
```

Note: I used to have an old (problematic) Ubuntu install on another partition which I deleted with GParted, (hence the Error 17 and this thread), and it's probably mentioned in the fstab but I'm too new to figure it out unfortunatly.

---

### Post by Elfy on 2008-06-25
So the menu.lst was right originally when it was pointed at 0,8.

It might be that > # groot=(hd0,5)

although I've never understood that. perhaps drs305 would. I know that my groot has always agreed with my boot.

---

### Post by ybd on 2008-06-25
> **forestpixie2 said:**
> So the menu.lst was right originally when it was pointed at 0,8.

It might be that 

although I've never understood that. perhaps drs305 would. I know that my groot has always agreed with my boot.

Hey thanks for the help, but I manually changed it while trying to get menu.lst to work. It used to be set to (0,8), and that didn't work.

---

### Post by drs305 on 2008-06-25
Your fstab is showing sda9 as root / , but the fdisk command shows sda9 as being a swap partition, which is confirmed by your gparted image.

For now, I would try making these revisions to see if you can get it to boot:

Comment out all your dev/sda9 and /dev/sda10 lines, then:

```

# dev/sda8 as root
/dev/sda8 / ext3 defaults,noatime,errors=remount-ro 0 1
# dev/sda9 as swap
/dev/sda9 none swap sw 0 0

```

This is all based on your ubuntu system being on sda8. Your grub setting would be (0,7). I'm guessing this based on the size of your partitions. You have a small 300MB partition. Did you have a separate /boot partition at one time?

groot should be set to the results of:
sudo grub
at the grub prompt:
find /boot/grub/stage1

---

### Post by Elfy on 2008-06-25
Yes I know now - reread (again) it wrong :)

That aside groot is pointing at (hd0,5) - those parts of menu lst aren't actually commented out - it is a working part of the menu.lst

> 
There is an option for groot in your menu.lst this should be set to where your current Ubuntu / partition is. For example if groot is

# groot=(hd0,0)
Then /dev/hda1 or /dev/sda1 MUST be where / is mounted


---

### Post by ybd on 2008-06-25
> **drs305 said:**
> For now, I would try making these revisions to see if you can get it to boot:

Just tried this, and made sure groot was correct (stage1 says it's (hd0,7) )

Unfortunatly it didn't work. Here's a copy/paste of my fstab, just to make sure I uncommented right, etc:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
# UUID=49ce7746-9e55-4331-96bc-1616845551b7 /               ext3    relatime,errors=remount-ro 0       1
# dev/sda8 as root
/dev/sda8 / ext3 defaults,noatime,errors=remount-ro 0 1
# dev/sda9 as swap
/dev/sda9 none swap sw 0 0
# /dev/sda10
# UUID=2007de55-53cf-42aa-9b79-23a2daed9257 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#Added by diskmounter utility
/dev/sda2 /media/sda2 ntfs ro,user,fmask=0111,dmask=0000 0 0
```

Again thanks for the help.

---

### Post by drs305 on 2008-06-25
If you mount /dev/sda8 on /temp1 and then do a "ls /temp1" do you see the normal ubuntu folders/files (e.g. bin, boot, etc, and vmlinuz)?

If you mount /dev/sda6 to /temp1 what files/folders are on that partition?

And in your menu.lst your # groot line says # groot=(hd0,7) and ubuntu is referenced to (hd0,7)

And just to confirm where we are: 
When you boot do you get the grub menu and can boot into windows?
If that's the case, when you select Ubuntu what happens?

---

### Post by biocyberman on 2008-06-25
I have this quick tips. I dealt with Error 17 of Grub many times and this tip helps me most of the time.
Here is how you find "X" as  you want:

On booting with grub, select the boot menu you want to boot in by up-down arrows, type "e" to edit that menu item. Select the line that look something like this: 
```

root		(hd0,X)

```

Type "e" again to edit that line. Replace X with one number i.e. 9 and hit "b" for booting. If number 9 doesn't work try other numbers. Remember the one that works and edit your menu.lst accordingly later. 

If this trick doesn't work. It means you may in to install grub again.And I will come back to that later you neccessary.

---

### Post by ybd on 2008-06-25
drs305: sda8 is fine and I can indeed see the normal folders with ls
After some tedious work it seems that sda6 is the 'leftover' partition from the old Ubuntu install (I'm not sure if it's the only leftover swap partition unfortunatly... sigh), and the only things in there are a couple of links to cd mount points (I think), an empty var folder, and an fstab file. Here's the content of that fstab if it's any use:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=671c23eb-58f5-4695-93a7-e56edbd5eb39 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=ad585ec7-59bf-42c2-a2ab-9297c8925431 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Unfortunatly I can't mount dev7 or dev9, the error for both is: "/dev/sda7 looks like swapspace - not mounted mount: you must specify the filesystem type".

---

### Post by ybd on 2008-06-25
biocyberman: Grub does not boot at all. Before loading the menu, right after the bios message the pc halts with "Grub Error 17" or something similar, and if there's a key that makes it boot to the menu anyway, I didn't find it.

---

### Post by biocyberman on 2008-06-25
@ybd: You may want to try this to reinstall grub: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I will take a closer look at your fstab later if reinstall grub doesn't work.

---

### Post by biocyberman on 2008-06-25
@ybd: You may want to try this to reinstall grub: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
I will take a closer look at your fstab later if reinstall grub doesn't work.

---

### Post by drs305 on 2008-06-25
> **ybd said:**
> biocyberman: Grub does not boot at all. Before loading the menu, right after the bios message the pc halts with "Grub Error 17" or something similar, and if there's a key that makes it boot to the menu anyway, I didn't find it.

I believe your partitions and fstab are set correctly. At this point you either need to sudo update-grub or reinstall it as suggested above.

---

### Post by ybd on 2008-06-25
Well good news and bad news. The good news is that Super Grub Disc worked, not to mention the kick *** interface ;-)))) I can't believe I spent over 4 hours when I could have done it in 10 minutes

The bad news is that apparently sda2 is now pretty much completely wiped, and I'm not sure if it's the partitioning (most likely) or the Grub discing because I haven't checked it after partitioning. GParted reports that it's just as nearly-full as it was before and Ubuntu does the same, but Ubuntu displays it as empty when I mount it and XP does display one of the folders the partition had, which strangely enough seems completely in tact.

Oh well the point is I'm done! :guitar: Thank you people for all the help, this is easily the best community I've ever seen.

---

