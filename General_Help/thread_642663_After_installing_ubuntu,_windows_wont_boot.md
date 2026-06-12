---
title: "After installing ubuntu, windows wont boot"
date: 2007-12-16
forum: General Help
---

### Post by drewg on 2007-12-16
Hi,
This is what I get from doing "sudo fdisk -l (smal L)
cat /boot/grub/menu.lst"

> Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1a321a31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        5738    46082452+   f  W95 Ext'd (LBA)
/dev/sda2   *        5739        9385    29294527+  83  Linux
/dev/sda3            9386        9733     2795310   82  Linux swap / Solaris
/dev/sda5               2        5738    46082421    7  HPFS/NTFS
drewg@drewg-desktop:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=97523eae-a0a9-4497-bf23-20f2858219c6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=97523eae-a0a9-4497-bf23-20f2858219c6 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=97523eae-a0a9-4497-bf23-20f2858219c6 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet



Now I know windows is there in sda5, and when I go into that partition, all my windows files and such are there, it's just that when I boot up, windows isn't showing up, as you can see above. I tried to do grub, to boot windows under linux, I have no idea how and searching really didn't help me find out how.

Basically, I booted from the windows CD, did a chkdsk, that didn't fix it. Neither did making my HD the first boot device. I try to do fixmbr in my terminal, I forgot the command, but it can't access the mbr. I will try to do fixmbr in the windows recovery console and I'll let you know how that goes.

But if anyone has suggestions, I'm ready and willing to try them, so please let me know how I can fix this.

thanks.

---

### Post by drewg on 2007-12-16
After doing a fixmbr I now get:
Error loading operating system

Which means I can't boot into windows XP or Ubuntu. 

Any ideas on how to fix this?

Is there any way I can access my HD via ubuntu live cd?

---

### Post by drewg on 2007-12-16
Ok, as per this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I get no file found / can't find file.

I access my linux partition, stage 1 is under grub.

What's the commands to restore it?

The linux partition is the smallest one, it's on an ext2 file system.

Also, how would I restore my windows boot as well?

---

### Post by torgrot on 2007-12-16
Take a look at Herman's page here [http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)
All is not lost since you can see stage 1 on your disk.  All you need to do is reinstall grub.  Although I am somewhat concerned that your windows installation appears to be in an extended partition which you can't boot windows from.  

torgrot

---

### Post by logos34 on 2007-12-16
like torgrot said all you need to do is restore grub to the mbr.  Like this

sudo grub

> find /boot/grub/stage1
(should output 'hd0,1' because root is sda2)
> root (hd0,1)
> setup (hd0)

Then add a windows entry to the bottom of menu.lst like this:

> title           Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader     +1

---

### Post by drewg on 2007-12-16
> **logos34 said:**
> like torgrot said all you need to do is restore grub to the mbr.  Like this

sudo grub

> find /boot/grub/stage1
(should output 'hd0,1' because root is sda2)
> root (hd0,1)
> setup (hd0)

Then add a windows entry to the bottom of menu.lst like this:

None of those commands work.

I did manage to get ubuntu back on the menu.lst by doing a few commands and writing the boot to the menu.lst through terminal.

When I go to edit the menu.lst in text editor:

> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

I will try editing it under ubuntu (non live cd). 
Although there is no way to login through the browser and allow me to edit such files. So there must be a way through terminal right?

---

### Post by drewg on 2007-12-16
Ok guys thanks thus far for your help.

When I try to boot up:

Boot disk failure, enter system disk and hit enter.

I enter ubuntu, yes it works fine, and nothing happens..
I enter win xp, same as above.

In bois, I have HD as both primary and secondary boot up (same hd, as I have only 1) I tried various numbers, and scsi (ubuntu thought my hd was scsi, so I thought that might help) with no success. So I have cd-rom as secondary, still nothing happening, just the same error.

I read on the net to go into the bios and see if it auto detects my HD. It does.

So, the current problems are:

A. Can't add new lines (for win xp) to the boot file (stage1)
B. Boot disk failure, enter system disk.....

I go into computer to look for the grub thing to see if ubuntu is still listed. 

There's only 1 filesystem listed instead of 2. 
In the 1 that's listed, under /boot/ there's no other folders, only the files listed:
/boot/abi-2.6.22-14-generic
/boot/config-2.6.22-14-generic
/boot/initrd.img-2.6.22-14-generic.bak
/boot/memtest86+.bin
/boot/System.map-2.6.22-14-generic
/boot/vmlinuz-2.6.22-14-generic

I'm running a 32 bit P4. And an 80GB Samsung IDE drive.

I don't know how these files suddenly disappeared

Under partition manager it finds the partitions:
Sda1
and Sda2

Both have errors "unable to detect file system" with some possible reasons.

Both are not mounted.

Still the above commands come with errors.

Any ideas?

---

### Post by logos34 on 2007-12-16
let's see, where were we (before the forums went offline so rudely!)...

you have to edit menu.lst as root, even on the live cd:

**sudo** gedit /media/disk/boot/grub/menu.lst (or wherever it's mounted)

or in terminal:

sudo nano -w /media/disk/boot/grub/menu.lst

So, those commands that you said don't work, have yu tried it without the 'find' part: 

sudo grub

> root (hd0,1)
> setup (hd0)
> quit

---

### Post by drewg on 2007-12-16
> **logos34 said:**
> let's see, where were we (before the forums went offline so rudely!)...

you have to edit menu.lst as root, even on the live cd:

**sudo** gedit /media/disk/boot/grub/menu.lst (or wherever it's mounted)

or in terminal:

sudo nano -w /media/disk/boot/grub/menu.lst

So, those commands that you said don't work, have yu tried it without the 'find' part: 

sudo grub

> root (hd0,1)
> setup (hd0)
> quit

```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd0,1)

Error 5: Partition table invalid or corrupt

grub> setup (hd0)

Error 12: Invalid device requested

grub> root (hd0,1)

```

The menu.lst file is empty.

What do I need to enter for ubuntu to work? I did update it when I'd finished installing it to the latest update.

For now I'll add windows

Uh oh
"Could not save the file /media/disk/boot/grub/menu.lst."
"Unexpected error: File not found"

As I said earlier: there is no ./grub in /boot/ just the files listed in my latest reply (bar this 1).

Doing the first command in terminal says that there is no menu.lst file (file not found).

In terminal it brings up some weird stuff, which doesn't work when I do the command for help it lists.

---

### Post by logos34 on 2007-12-17
Ok, you posted just before I did...

if there's no grub folder with menu.lst, stage1 et al, then reinstalling grub using the catlett howto won't work...My advice is to reinstall.

Were you able to boot from windows on that logical partition before you installed ubuntu?  Because torgrot is right--at least, that is, if there's no prexisting active windows partition containing the ntldr boot files (I can boot xp home, for instance, on a logical only if another 'master' xp is on the first (primary) partition with the bootloader files).

---

### Post by drewg on 2007-12-17
> **logos34 said:**
> Ok, you posted just before I did...

if there's no grub folder with menu.lst, stage1 et al, then reinstalling grub using the catlett howto won't work...My advice is to reinstall.

Were you able to boot from windows on that logical partition before you installed ubuntu?  Because torgrot is right--at least, that is, if there's no prexisting active windows partition containing the ntldr boot files (I can boot xp home, for instance, on a logical only if another 'master' xp is on the first (primary) partition with the bootloader files).

No I wasn't able to boot windows after i installed Ubuntu.

Can you tell me how to add windows xp to the startup list so I can have that atleast?
I suppose I should do a fix MBR, I will try that. As listed on the GRUB page.
i will let you know how that goes shortly.

And then I will re-install ubuntu.
Or should I reinstall grub?
I can't find on the grub page how to reinstall it.

But what about the partitions not being mounted?

---

### Post by logos34 on 2007-12-17
> **drewg said:**
> No I wasn't able to boot windows after i installed Ubuntu.

Can you tell me how to add windows xp to the startup list so I can have that atleast?

Menu.lst is what grub displays at startup.  But it doesn't exist so you can't add windows to it.

Yeah, go ahead and try fixmbr, see if you can boot xp.  Doubt it.  So you're probably looking at reinstalling both OS's--windows first (on a **primary** this time), then ubuntu (which can be inside extended on logical partition).  Let it install grub to the default location (mbr)...hopefully this time the grub folder in /boot won;t be left out!

---

### Post by logos34 on 2007-12-17
I really gotta go now...it's late.  be back tomorrow.

---

### Post by drewg on 2007-12-17
Fixmbr did nothing.
I still have the boot disk problem.

I wasn't planning to install ubuntu again, but I got Eve and it works on linux so I did.

I will re-install ubuntu so I can access my windows files.

Looks like all my partitions are formatted... Somehow.
As while installing it lists free space as my whole hd size.

Weird. I wonder how it formatted its self.

---

