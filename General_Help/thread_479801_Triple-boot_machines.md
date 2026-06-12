---
title: "Triple-boot machines"
date: 2007-06-20
forum: General Help
---

### Post by chankarwing on 2007-06-20
I have 2 windows and (obviously) ubuntu. When it gets to the bootup part, the selections i can choose are:

Windows Operating System(s)
 1)Windows XP 1
 2)Windows XP 2
Ubuntu Linux
Ubuntu Linux Recovery Mode

Basically I have another bootup selection under Windows Operating System(s) if I select it. So I want to change it so all OS are put into one bootup selections, which should look like the following below:

Windows XP 1
Windows XP 2
Ubuntu Linux
Ubuntu Linux Recovery Mode

---

### Post by poohbear1616 on 2007-06-20
Huh!!??
I'm assuming you mean your grub choices.
Grub is your boot manager and it boots what you pick from the list.

> So I want to change it so all OS are put into one bootup selections

Are you saying there is something not showing in the boot options?

---

### Post by chankarwing on 2007-06-20
> Windows Operating System(s)
1)Windows XP 1
2)Windows XP 2

Lets say Windows XP 1 and 2 cannot be seen but only Windows Operating System(s) can be seen on the linux bootup screen along with unbuntu.

When I select Windows OS from the menu, it then takes me to another bootup screen, but this time its asking me to select Windows XP 1 or 2.

But i dont want that. I want it so that:

Windows OS...is gone (this is a chainloader by the way, if that helps)
Windows XP 1 and 2 AND ubuntu to show on the linux bootup screen. Basically I will have 3 choice of OS to choose from on bootup.

---

### Post by poohbear1616 on 2007-06-20
```
cat /boot/grub/menu.lst
```

Please post output.

---

### Post by chankarwing on 2007-06-20
All i want is to add 2 more Windows XP on GRUB instead of having 2 bootscreens. So every OS i have will be listed in GRUB and will be selected from GRUB. Not Windows but the GRUB =) It sounds really easy but I have no experience on Ubuntu.

> changavin@ubuntulinux01:~$ cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# kopt=root=UUID=913fb22d-d125-4693-9ec9-44d08a29b19d ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=913fb22d-d125-4693-9ec9-44d08a29b19d ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=913fb22d-d125-4693-9ec9-44d08a29b19d ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

As you can see it is default but then again I tried editing it myself previously but manage to screw it up =) so i decided to start again and probably this will make it easy :p

---

### Post by poohbear1616 on 2007-06-21
Ok, one more thing needed.
output of this:

```
sudo fdisk -l
```

---

### Post by chankarwing on 2007-06-21
Here is the output:

> Disk /dev/hdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        5502    44194783+   7  HPFS/NTFS
/dev/hdc2            5503        9964    35841015    f  W95 Ext'd (LBA)
/dev/hdc5            5503        7413    15350076    7  HPFS/NTFS
/dev/hdc6            7414        9964    20490876   83  Linux

---

### Post by poohbear1616 on 2007-06-21
One other question.
Are all these on the same drive?
If they are it gets a bit tricky!

---

### Post by poohbear1616 on 2007-06-21
Nevermind, you posted at the same time I did.

---

### Post by chankarwing on 2007-06-21
Yup it is

---

### Post by Marious on 2007-06-21
I assume what you are seeing is Grub First then the Windows Boot Version or are you choosing Windows and then Grub goes to another Grub menu that has Windows 1 and 2?

---

### Post by chankarwing on 2007-06-21
Yup Yup :D

---

### Post by poohbear1616 on 2007-06-21
To boot straight from the first screen you'll have to hide and unhide the partitions
for each windows selection.
You'll have to do this manually.
I'll point you [[COLOR="Red"]here[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows") to see what I am getting at.

---

### Post by chankarwing on 2007-06-21
Basically its copying this to command line on GRUB? right?

```

     grub> unhide (hd0,0)
     grub> hide (hd0,1)
     grub> rootnoverify (hd0,0)
     grub> chainloader +1
     grub> makeactive
     grub> boot

```

---

### Post by poohbear1616 on 2007-06-21
Yeah....somewhat.

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 5502 44194783+ 7 HPFS/NTFS ----------------------  Three
/dev/hdc2 5503 9964 35841015 f W95 Ext'd (LBA)-----------------Different windows
/dev/hdc5 5503 7413 15350076 7 HPFS/NTFS----------------------Here? right.
/dev/hdc6 7414 9964 20490876 83 Linux

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title Windows NT/2000/XP (loader)
unhide (hd0,0)
hide (hd0,1)
hide (hd0,4)
rootnoverify (hd0,0)
chainloader +1
makeactive
boot

#blah blah on /dev/hdc2
title windows (whichever one)
hide (hd0,0)
unhide (hd0,1)
hide (hd0,4)
rootnoverify (hd0,0)
chainloader +1
makeactive
boot

#blah on /dev/hdc5
title windows (something)
hide (hd0,0)
hide (hd0,1)
unhide (hd0,4)
rootnoverify (hd0,0)
chainloader +1
makeactive
boot

I believe this is what you want.
May have to fine tune it a bit.

---

### Post by poohbear1616 on 2007-06-21
Ok.I'm tired and maybe having a dumb attack.
Reviewing your first post made me rethink things.
Is this:
/dev/hdc2 5503 9964 35841015 f W95 Ext'd (LBA)

a data partition or a windows OS?

If data I'll have to change what I threw up on 
the last post.

---

### Post by chankarwing on 2007-06-21
It didnt work

/dev/hdc1 * 1 5502 44194783+ 7 HPFS/NTFS ---------------------- Windows 1
/dev/hdc2 5503 9964 35841015 f W95 Ext'd (LBA)----------------- Extended
/dev/hdc5 5503 7413 15350076 7 HPFS/NTFS---------------------- Windows 2
/dev/hdc6 7414 9964 20490876 83 -----------------------------------Linux

The 2 windows option added got me to another bootloader and then an error screen of windows..something about auchk.

The loader no such partition

And Linux just didnt want to load at all :S

---

### Post by chankarwing on 2007-06-21
Would this be easy?

Shrink the time on Linux GRUB so it will go over to Windows Bootloader
And then from the bootloader, I can choose either the 2 windows or ubuntu linux?

Maybe this will save the hassle you have to do in GRUB

---

### Post by poohbear1616 on 2007-06-21
Yeah.......If you wanna go that route.

this line in your grub menu can be changed:
timeout 10
10=10 seconds of course
set it to 1,2,3,4...etc
set it to 0 and it'll be a flicker......lol

---

### Post by chankarwing on 2007-06-21
what do i put in boot.ini then ? lol

---

### Post by poohbear1616 on 2007-06-21
But you'll have to move the windows selection in the grub menu
to the first on the list.

---

### Post by chankarwing on 2007-06-21
i have done that :)

---

### Post by newblacknoise on 2007-06-24
Hi, I am in the exact same situation as chankarwing. I have two copies of Windows XP installed (one for work, one for play) as well as Ubuntu 6.10. They are all on the same hard drive on my laptop. When I start my laptop, I get the GRUB which includes one selection for Ubuntu and one for WIndows XP (loader). If I select the Windows XP (loader) option, I get taken to the Windows Boot screen, which then lets me choose between my two copies of XP. I would like all 3 OS options to be on the GRUB menu, as it would be nice and neat :).

The sample code posted by poohbear1616 is a bit confusing, as I can't see any differences between the GRUB option for XP v1 and the GRUB option for XP v2.

I will post the output of my "sudo fdisk -l" command:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/hda2            2612        9729    57175335    f  W95 Ext'd (LBA)
/dev/hda5            2612        5222    20972826    7  HPFS/NTFS
/dev/hda6            5223        6527    10482381   83  Linux
/dev/hda7            9605        9729     1003999+  82  Linux swap / Solaris
/dev/hda8            6528        9604    24715971    b  W95 FAT32
```

Here is what is on each device:
hda1 = XP v1
hda2 = an extended partition which contains hda5-hda8
hda5 = XP v2
hda6 = Ubuntu
hda7 = Ubuntu swap
hda8 = FAT32 partition used to share info between all 3 OSs

I'm going to keep searching for the right way to do this, but if anyone wants to help me out, I'd greatly appreciate it! :)

---

### Post by newblacknoise on 2007-06-24
OK, well, I screwed up bad, even for me.

I re-read poohbear1616's suggestion, and realised what it was trying to do (or so I thought). I gave it a go, adjusting the code to suit my system. It didn't work, and now I can't boot into anything without the Ubuntu LiveCD. I think it has something to do with the hide/unhide stuff, because I can no longer find a whole bunch of my partitions. I was going to throw in the towel and just reinstall Ubuntu, but found that gParted no longer recognises all the different partitions within the logical partition, it just sees one big ext3 partition. This means I would have to reinstall not one, but THREE operating systems, and the thought of that makes me want to cry.

Unfortunately I can not post the contents of my new menu.lst file that killed everything, because I can't figure out how to even find the partition it's on. Does anyone know how to get all the partitions "unhidden"? I've tried using the GRUB command line and calling the 'unhide' command on all the partitions, but it just keeps coming back saying that it's the wrong type, or it doesn't exist.

If I don't figure it out soon, I'll just have to start fresh and reinstall everything again, as I've got work that needs doing, and I can't afford to mess around too much longer. However, that is a last resort. Any help would awesome!

EDIT: I ended up restoring the Windows boot loader, which helped me get access to XP v1, but not to Ubuntu and XP v2, so I just bit the bullet and reinstalled them. It didn't end up taking that long after all, but I would still like to figure out how to put all 3 OSs onto the one GRUB boot menu, so if anyone has any ideas - please let me know. I'm pretty hesitant to start messing around with the GRUB again without sound advice! :)

---

