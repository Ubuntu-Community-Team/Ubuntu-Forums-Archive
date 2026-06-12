---
title: "Grub 1.5 error21"
date: 2007-11-03
forum: General Help
---

### Post by wildchild247 on 2007-11-03
Hello to all fellow Linux users

I am new to using linux and I am using ubuntu 7.1 gutsy gibbons

I installed ubuntu onto an external hard drive it boots up fine 

but I have windows vista on the internal hard drive and it gives me that error message

loading grub 1.5 please wait error21

any solutions to this problem

---

### Post by Prospero2006 on 2007-11-03
The grub boot loader is controlled by:

/boot/grub/menu.lst

You need to check that file for accuracy first of all.

There is also a process where you can use a live cd like knoppix
to go in and manually reinstall the mbr using the grub> command
interface.

Pros

---

### Post by meierfra on 2007-11-03
Post the output of

```
sudo fdisk -l
```

and 

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by wildchild247 on 2007-11-03
Thanks for the quick response guys

But this is my first time using linux and I even have problems installing stuff

Could you simplify please

Cheers guys

---

### Post by meierfra on 2007-11-03
Open a terminal (Applications>Accessories->Terminal). Type  the first command  I gave you and press enter.

It will ask you for your login password. Type the password (While  you type the password it will look like nothing is happening. That  is normal)  Press enter.  Post the output here (Use copy and paste)

Now type the second command in the terminal. A small window will pop up. Enter your password and press enter. A new larger window will appear.  It contains the file "/boot/grub/menu.lst"  Select the whole contents and post it here.

Once we see this information, we should be able to tell you exactly  how to edit the file "menu.lst" to fix your problem.

---

### Post by eph1973 on 2007-11-03
Try going to Applications>Accessories>Terminal
When the screen pops up, type into the screen the following command:
```
cat /boot/grub/menu.lst
```copy and paste the output of that (it will be somewhat lengthy, but you should be able to grab everything that comes up with copy) to your reply.  Make sure before you paste it into the reply, you type ["code"] (with the brackets, but without the quotation marks, of course) then at the end, type ["/code"].
Repeat the process, but this time when you go to the terminal type:
```
sudo fdisk -l
```Remembering to wrap your response with the code tags again.

You may find [this link]("http://www.mepis.org/node/7330") helpful, also.

---

### Post by wildchild247 on 2007-11-03
```

alanheung@alanheung-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        1318    10485760    7  HPFS/NTFS
/dev/sda3            1318       11044    78125000    7  HPFS/NTFS
/dev/sda4           11044       14594    28511232    f  W95 Ext'd (LBA)
/dev/sda5           11044       14594    28510208    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd44fc693

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121224   973731748+  83  Linux
/dev/sdb2          121225      121601     3028252+   5  Extended
/dev/sdb5          121225      121601     3028221   82  Linux swap / Solaris
alanheung@alanheung-laptop:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied

```

---

### Post by meierfra on 2007-11-03
The command was 

gksudo  gedit /boot/grub/menu.lst

not just

/boot/grub/menu.lst

("cat  /boot/grub/menu.lst" works too)

---

### Post by wildchild247 on 2007-11-03
```

alanheung@alanheung-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=37fe060d-0f5d-42cc-ad37-338e413912bc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=37fe060d-0f5d-42cc-ad37-338e413912bc ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=37fe060d-0f5d-42cc-ad37-338e413912bc ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Dell Utility Partition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

alanheung@alanheung-laptop:~$ 

```

---

### Post by meierfra on 2007-11-03
Open the file "/boot/grub/menu.lst"

via

```
gksudo gedit /boot/grub/menu.lst
```

(Opps: It seems I left out the gedit the last time)

Add this to the end of the file:


title          Windows Vistas
rootnoverify           (hd0,1)
savedefault
makeactive
chainloader     +1

Save the file and Windows XP should appear on the grub menu  after reboot.

---

### Post by meierfra on 2007-11-03
Edited my last post. Forget that you had vistas and not XP ( allthough original solution probably worked too)

---

### Post by meierfra on 2007-11-03
One more comment: 

All of this will only works if  your external drive is plugged in.
If you want, it can set it up so that  Vistas also boots without  the external drive plugged in. Just let me know and I show you how to do it.

---

### Post by wildchild247 on 2007-11-03
Yeah it works 

So if I unplug the hard drive Windows Vista doesnt boot up

Could you show me how to allow windows vista to boot up without the external HD

thanks I really appreciate the help

---

### Post by meierfra on 2007-11-03
O.K. But I got to leave now. I will be back in an hour or so.

---

### Post by wildchild247 on 2007-11-03
No problem 

You have been such a great help that I can wait till you get back

---

### Post by wildchild247 on 2007-11-03
I noticed the way when I was in windows vista

I wasn't able to access the external HD

I usually store all my movies and music on the external HD

Is there a way when I am in windows to access all the files on the external?

---

### Post by meierfra on 2007-11-03
> Is there a way when I am in windows to access all the files on the external? 

You can use fs-driver ([http://www.fs-driver.org]("http://www.fs-driver.org")) It 
works well for Windows XP, But it seems to be a bit buggy in Vista.  Might be better to create a separate ntfs partition on your external drive.

Getting vista to boot on without the external drive takes a little bit of work.

This is what needs to be done:

1) Set  your bios to boot from the external drive first

2) Install  Grub to the MBR   of external drive.   (The MBR is just the first 512bytes of a drive)

3) Edit "menu.lst" to reflect the new set up.

4) Reinstall vistas bootloader  to the MBR of your internal drive. 


For 1)  Let me know if you need help with changing the boot order. 

For 2) and 3) I need some information first:

After you changed the boot order,  boot   from the Ubuntu live cd.  Open a terminal, type 
"sudo fdisk -l"  ( same command as before, but it won't asked for a password.) Post the output.


4) will be easiest if you  a Vista  DVD (or CD). Booting from the Vista DVD should give you an option to repair the MBR or the Bootsector.


If you don't have the Ubuntu Live CD or the Vista DVD, we will have to revise the plan.

---

### Post by wildchild247 on 2007-11-03
I went into the BIOS and made the internal HD 1st in the boot sequence

I used the live cd to get this info

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78000000

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        1318    10485760    7  HPFS/NTFS
/dev/sda3            1318       11044    78125000    7  HPFS/NTFS
/dev/sda4           11044       14594    28511232    f  W95 Ext'd (LBA)
/dev/sda5           11044       14594    28510208    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd44fc693

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121224   973731748+  83  Linux
/dev/sdb2          121225      121601     3028252+   5  Extended
/dev/sdb5          121225      121601     3028221   82  Linux swap / Solaris
ubuntu@ubuntu:~$

```

2) Install Grub to the MBR of external drive. (The MBR is just the first 512bytes of a drive) I dont know how to do this

3) Edit "menu.lst" to reflect the new set up. I dont understand what to do here
4) I have the Ubuntu Live Cd and I have a Dell version of Windows Vista

---

### Post by meierfra on 2007-11-03
Slight confusion. We need to have the external drive first. Is that what it  used to be? Then go back  to  the  bios. Set the external drive  first. Boot  into ubuntu (the regular  ubuntu not the Live) and  let me know.

---

### Post by wildchild247 on 2007-11-03
It was external HD first

Ok so I will put the external HD first in the BIOS

and just load up Ubuntu normally

---

### Post by meierfra on 2007-11-03
> 2) Install Grub to the MBR of external drive. (The MBR is just the first 512bytes of a drive) I dont know how to do this

3) Edit "menu.lst" to reflect the new set up. I dont understand what to do here


I'll give you detailed instructions for theses soon. But first I need to be sure what the boot order  was before you changed it.

---

### Post by meierfra on 2007-11-03
Ok. I'm writing the instructions, but it might take a while

---

### Post by meierfra on 2007-11-04
Boot into   ubuntu (the regular ubuntu, not the live cd) (if you already are using ubuntu, skip this step)

Open menu.lst via "gksudo  gedit /boot/grub/menu.lst" (just as before)

1) Change all   (hd1,0) to (hd0,0) 

There will be four (once "#groot (hd1,0)" and three times "root (hd1,0)"

2)

Change the windows vista item to

title Windows Vistas
rootnoverify (hd1,1)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

3)    change the Dell item to
title           Dell Utility Partition
root            (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader     +1

Save the file.


Open the file /boot/grub/device.map via

gksudo gedit /boot/grub/device.map

and  change it so that it reads

(hd0) /dev/sdb
(hd1) /dev/sda

Save the file.


In the termial type

sudo grub --device-map=/boot/grub/device.map

hit return. You will get a grub prompt:

grub>

Type 

root (hd0,0)

setup (hd0)

quit.


Reboot and report back here (if things did go wrong, you might not be able to boot into ubuntu anymore. Then just use the Live CD.)

---

### Post by wildchild247 on 2007-11-04
OK it was initially

1.internal HD
2.USB storage device (external HD)
3.diskette drive
4.DVD/CD drive

I switched it to this afterwards
1.USB storage device (external HD)
2.internal HD
3.diskette drive
4.DVD/CD drive

when I booted up it said OS was missing

so I am back to the original boot up beginning with the internal HD

---

### Post by meierfra on 2007-11-04
I just fixed a typo. I hope its not to late.

---

### Post by meierfra on 2007-11-04
FYI: I changed "grub  --device-map=/boot/grub/menu.lst" to  
"grub --device-map=/boot/grub/device.map"

---

### Post by meierfra on 2007-11-04
OK. hang on. I'll revise my instruction

---

### Post by wildchild247 on 2007-11-04
the last part came up with this

```
alanheung@alanheung-laptop:~$ sudo grub --device-map=/boot/grub/menu.lst
/boot/grub/menu.lst:14: error: No open parenthesis found

```

ok I'll stop doing what im doing till you finish

---

### Post by meierfra on 2007-11-04
Actually  the instruction are the same. Just  at the very end when you reboot, change the boot order so that the external drive comes first.

---

### Post by meierfra on 2007-11-04
> anheung@alanheung-laptop:~$ sudo grub --device-map=/boot/grub/menu.lst
/boot/grub/menu.lst:14: error: No open parenthesis found

That was my typo: it needs to be  sudo grub --device-map=/boot/grub/device.map

---

### Post by meierfra on 2007-11-04
Things got a little confusing with my "typo" and your mixed up statements about the "boot order". But as far as I see it, everything should be in place now.

---

### Post by meierfra on 2007-11-04
Just to summarize:  This is what you still need to do:

sudo grub --device-map=/boot/grub/device.map

hit return. You will get a grub prompt:

grub>

Type

root (hd0,0)

setup (hd0)

quit


While rebooting, change the boot order so that the external  drive is first.  Report back here (if things did go wrong, you might not be able to boot into ubuntu anymore. Then just use the Live CD.)

---

### Post by wildchild247 on 2007-11-04
I inputed all the code

but when I reversed the boot order so that the external was first

its say unable to mount partition

I am using the live cd now

---

### Post by meierfra on 2007-11-04
Did the error occur  after you selected ubuntu on the grub menu, or did the grub menu not even appear?

---

### Post by wildchild247 on 2007-11-04
grub menu didnt appear

is it possible for me to get back onto ubuntu without the live CD

---

### Post by meierfra on 2007-11-04
Let's to a temporary fix:

We will edit menu.lst one more time. Since you are on the live cd, you need to mount  your ubuntu partition first:


in a terminal

sudo  mkdir /media/sdb1

sudo mount -t ext3 /dev/sdb1 /media/sdb1

gksudo gedit /media/sdb1/boot/grub/menu.lst

Just change one of the (hd0,0) back, namely

title           Ubuntu 7.10, kernel 2.6.22-14-generic 
root            (hd0,0)

back to

title           Ubuntu 7.10, kernel 2.6.22-14-generic 
root            (hd1,0)


If you reboot with the internal drive first in the bios , you should be able boot back into ubuntu.
(we really should have back up your menu.lst before we started messing with it)

---

### Post by meierfra on 2007-11-04
If this did not work change all the (hd0,0) back to (hd1,0). 
and 

  
sudo grub 
root (hd1,0)
setup (hd0)
quit

And try rebooting with the internal hard drive first in the bios.

---

### Post by wildchild247 on 2007-11-04
ok that worked

and now the internal HDD is the 1st in the boot sequence

and im not running from the live CD

---

### Post by wildchild247 on 2007-11-04
Am I back to the position where I can run windows but only if I have the external hard drive plugged in

---

### Post by meierfra on 2007-11-04
Change  the windows item in menu.lst back to 

title Windows Vistas
rootnoverify (hd0,1)
savedefault
makeactive
chainloader +1


I'm going to bed now but I'll be back here once I figured out what went wrong and what to do next,

---

### Post by wildchild247 on 2007-11-04
no problem you have been a great help

Im sure we can fix it no bother

---

### Post by wildchild247 on 2007-11-04
Just wondering if anyone online can figure out a solution

dont forget that I am new to using linux so I am not familiar with some terms

cheers

---

### Post by meierfra on 2007-11-05
Sorry for the delay. I spend Sunday in bed with a nasty cold.

Well, I still don't know what went wrong, but I found one place where I should have requested more information from you to make sure that things are the way they seem to be.  There is also a  place where even a small typo on your side could have caused the problem. 

So I suggest that we go through the whole process again, but adding a few safety rails.

Also  I will give you some background information, so that  the commands you are typing at least make some sense to you.

Grub (the program in charge of booting)   and Ubuntu have different names  for the hard drives. Ubuntu calls them sda and sdb. Grub calls them (hd0) and (hd1).  Grub always starts counting are zero. So (hd0) just stands for the first hard drive and (hd1) for the second. Similary (hd0,1) stands for the second partition on the first hard drive.
Grub tries to  name the  drives in the boot order,  but  its does not always get it right. 

Currently I believe the names are as follows:

internal drive=windows drive=sda=(hd0)=first drive in boot order
external drive=ubuntu-drive= sdb= (hd1)=second drive in boot order.

Looking at the information from "sudo fdisk -l" one can see that sda  is a 120 GB  windows drive and  sdb is the 1000 GB ubuntu drive.

Now go  to the Grub prompt via

sudo grub

Type

find  boot/grub/menu.lst

Grub now looks through all the partitions on your hard drive searching for the file "/boot/grub/menu.lst" and will list all the partitons where it found this file.
This file is  on your ubuntu partition, the first partition on the second hard drive. So grub
should return

(hd1,0) 

Type "quit" to exit the Grub prompt.

Next lets  verify the boot order in your bios.
On my computer (a Dell)  I can press F12 to choose which drive to boot from:  but this only applies to this  one boot,  and the order in which the hard drives are displayed is not the boot order. I can also press F2  to get into the bios setup. This lets me see the boot order and  any changes  are  permanent (that is, until the next time one changes the boot order in the bios)

Next we want to find out whether the grub names for the hard drive, when we change the boot order in the bios:

 Change the  boot order in the bios such that the  external drive is first. 
Make sure that you changed the boot order permanently.

Since you won't be able get into ubuntu  with this boot order, we will have to use
the ubuntu Live CD.  So boot from the ubuntu Live CD. Do

sudo fdisk -l

 This should give the same exact output as before. (But let me know if it didn't)

Next

sudo grub
find /boot/grub/menu.lst


This should return (hd0,0) or (hd1,0).

Since I'm not sure which one it is going to be, I'll wait for your response before continuing  my instructions.

---

### Post by wildchild247 on 2007-11-05
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find "boot/grub/menu.lst"

Error 15: File not found

grub> 

```

I tried the first part of the instructions and heres what I came up with

Cheers on the info as it helps me understand linux better

---

### Post by meierfra on 2007-11-05
My bad. The quotations marks shouldn't be there:

find /boot/grub/menu.lst

---

### Post by wildchild247 on 2007-11-05
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        1318    10485760    7  HPFS/NTFS
/dev/sda3            1318       11044    78125000    7  HPFS/NTFS
/dev/sda4           11044       14594    28511232    f  W95 Ext'd (LBA)
/dev/sda5           11044       14594    28510208    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd44fc693

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121224   973731748+  83  Linux
/dev/sdb2          121225      121601     3028252+   5  Extended
/dev/sdb5          121225      121601     3028221   82  Linux swap / Solaris

```

```
grub> find /boot/grub/menu.lst
 (hd1,0)

grub> 
```

please bear with my replies as I am using the schools internet and its really slow

---

### Post by eph1973 on 2007-11-06
In order to do dual boot with Linux without needing the external hard drive plugged in, you are going to need to blow up the GRUB install on your internal hard drive.  This can be achieved by putting in your Vista CD/DVD and booting up with it.
From there, click on "Repair your Computer"
Select your Vista installation, and then click "Next >"
Click on command prompt
At the prompt type
```
Bootrec /FixMBR
```then type exit.
Remove the Vista CD/DVD from your computer, and reboot
From here, you have two choices:

1) You should be able to boot into Vista with or without your external HD attached.  If you wish to boot into Ubuntu, change the boot order at your BIOS splash screen to boot into Ubuntu.  If you want to boot into Vista, boot without your external hard drive installed or by changing the boot order again in the BIOS.

2) Changing the boot order to look for your USB hard drive first.  You will need to reinstall GRUB onto your boot sector of your _external_ hard drive.  By changing the boot order in your BIOS, boot into Ubuntu.  I can see what you need by what you have provided so far.  Assuming you are able to boot into Ubuntu, type:
```
sudo grub
```At the prompt type:
```
root (hd1,0)
setup(hd1)
quit

```Now type
```

gksudo gedit /boot/grub/menu.lst
```Go to the bottom of your menu.lst file.  All the places where you see root (hd1,0) for your Ubuntu partitions, change that to (hd0,0)
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=37fe060d-0f5d-42cc-ad37-338e413912bc ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=37fe060d-0f5d-42cc-ad37-338e413912bc ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin

```And change the Vista portion of your menu.lst to (hd1,0)
```

title           Dell Utility Partition
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```Save the file and exit.

You need to reverse them like that because when your external drive becomes the first drive to boot, to GRUB it thinks it is (hd0), so you gotta tell it to switch them around.

Now if your particular BIOS allows you to select a USB device to boot from with or without it plugged in, you are in business.  However, if your BIOS treats your external hard drive as just another hard drive, you can change the boot order in BIOS, but if you boot up with it unplugged, it will boot to Vista, and the next time you boot up, you will have to tell it about your USB hard drive again (that's the case with my old junk), or else you will have trouble booting into Ubuntu.

If you cannot boot into Ubuntu right now (i.e. you need to use the Live CD to boot into Ubuntu), let me know, then you have to do a couple of extra things.  If you have removed GRUB altogether, that's fixable, too.  Hope this helps.

---

### Post by meierfra on 2007-11-06
Both of your outputs have been exactly as I expected. I guess that is good, but it also means that we are not any closer to finding the  mistake. I don't have much time right know, so I just give you the next step:

boot into the regular ubuntu (so you need to change the boot order back to internal drive first)

Open a terminal and change to the directory /boot/grub via:
```

cd /boot/grub
```

backup the while "menu.lst" via

```
sudo cp menu.lst  menu.lst.backup
```

open "menu.lst" via

```
gksudo gedit menu.lst
```
(note here what you  only need to type "menu.lst"  instead of "/boot/grub/menu.lst" since  we are currently working in the directory "/boot/grub:


Now edit "menu.lst" exactly as I told you to the last time (see post #23))

Explanation for these changes:

1) root (hd1,0):  If you click on "ubuntu"   in the grub menu at boot-up, the "root (hd1,0)" statement tells grub to "mount" the partition "(hd1,0)" 
   But (hd1,0) stands for the first partition on the second hard drive. Since we will change the boot order such that  the external drive is first, Ubuntu will be on the first partition of the first hard drive. So we need to use "root (hd0,0)" in place of  "(hd1,0)"

2)  #groot (hd1,0):  The # in front of groot (hd1,0) tells grub to ignore this statement during boot-up,  So why would we change it?  Every time there is a kernel up-grade, your menu.lst will be automatically up-dated. The "groot" statement tells the up-date program what to use for "root" . So if we don't change #groot (hd1,0) to #groot (hd0,0), then during the next kernel-upgrade all the  root (hd0,0) statements would be replaced by root (hd1,0).


3) rootnoverify (hd1,1) 
   chainloader +1

This tells grub to turn control over to a program (chainloader) located on the 1 sector ( +1)  of  on the   second partition of the second hard drive (hd1,1)
Note that this is where windows is located, then the internal drive is first in the boor order. So  these command just put  the windows boot loader in charge of booting.  And since we changed the boot order we need to change (hd1,1) to (hd0,1)

4) map (hd0) (hd1)
    map (hd1) (hd0)

This tells the chainloader (the  windows boot loader) that windows is no longer on the first hard drive , but on the second

Will be back later with more instruction.

---

### Post by meierfra on 2007-11-06
I'm back.

We now have to edit the file /boot/grub/device.map. 
Why do we need to do that:
When you did "find /boot/grub/menu.lst" from the Live CD, the output was (hd1,0). That means that grub thinks that ubuntu was  on the second hard drive. But it was not, we switch the boot order and  ubuntu  was on the first hard drive. So we have to let grub know that ubuntu is really on the first hard drive.

```
gksudo gedit  /boot/grub/device.map
```

This will open  up the file  "device.map"

Edit the file so that it looks like

(hd0) sdb
(hd1) sda

Actually you shouldn't have to edited it, since you   already  did that in our first attempt. So just make sure that it is correct. 

If you want you can now post  "menu.lst" and "device.map", so that I can check for misprints before you proceed,

Next we will install Grub to the mbr of the external drive:
 Reboot your computer  using the Ununtu Live CD. But  change the boot order such that the external drive ist first. (Again make sure that you change it permanently, that is not only for a one time boot)

 (Last time we used the regular ubuntu for this step, I don't see anything wrong  with that  but just as an extra precaution, I want the external drive to be first in the boot order while we install grub. So we need to use the Live CD.)

In a  terminal type:

```
sudo mkdir /media/sdb1
``` 
This creates a  directory (=folder) with the name sdb1 inside the  directory  /media.

```
sudo mount  -t ext3 /dev/sdb1  /media/sdb1
```
This allows us  to access the files  on the ubuntu partition from the Live CD. All the files and folders from the ubuntu partition can now be found in  directory /media/sdb1.

```
sudo chroot /media/sdb1
```

This has the effect that all command from now on will be executed by the ubuntu partition and not the Life-CD.  Basically every thing we do from now on will be the same as if we would have booted directly into  the ubuntu partition.


```
 cd /boot/grub
```
as before this changes the current directory to /boot/grub

```
grub --device-map=device.map
```

This gets you to the grub prompt and tells grub to use "device.map".

```
find /boot/grub/menu.lst
```

I added this step as a precaution.  It should return (hd0,0). (Since the device.map tells grub that "sdb" (the ubuntu drive) is (hd0)

If you  get (hd1,0)  you probably have  a typo in "grub --device-map=device.map"
In this case type "quit"  and try again.

```
root (hd0,0)
```

```
setup (hd0)
```

These  two step tell grub to install a small program  to the MBR of (hd0). Note here that according to the device.map (hd0) is sdb, your external drive. This small  program  will tell the computer  at boot-up to  look for the grub menu (/boot/grub/menu.lst") on the partition (hd0,0). (Which  according to the device.map will be the first partition on sdb)

Before exiting Grub,  copy the whole contents of the terminal and post it here (just so that I can see any error messages you might have gotten)

```
 quit 
```




Reboot and hopefully you will be able be boot into ubuntu.

But you won't be able to boot into windows without the external drive yet. We'll take care of that once you successfully booted into ubuntu from the external drive.

---

### Post by meierfra on 2007-11-06
Just in case things go wrong again. This will let you boot into Ubuntu again:

Boot into the Life CD with the internal drive first in the boot order.

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
cd /media/sdb1/boot/grub
sudo cp menu.lst  menu.lst.external   
sudo cp menu.lst.backup menu.lst
sudo grub
root (hd1,0)
setup (hd0)
quit

```


"sudo cp menu.lst  menu.lst.external"  saves the current menu.lst, in case we want to try again.
 
"sudo cp menu.lst.backup menu.lst" restores the  menu.lst we saved earlier.

---

### Post by wildchild247 on 2007-11-06
when I am at this stage using the Live Ubuntu CD

```
find /boot/grub/menu.lst
```

it returns error 15 cannot find file

note: I used the final post solution, reversed the order of the drives and I am using ubuntu normally

---

### Post by Ubumby on 2007-11-06
I had the exact same problem when I first installed ubuntu. What helped me was I downloaded Super Grub Disk and put it onto a cd (live cd)

[http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download")

I then just fixed my windows boot on my first harddrive than re-installed ubuntu on my other harddrive. I do this before every clean install of ubuntu. I don't know if this will help you as much as it helped me but I would suggest trying it. Good Luck.

---

### Post by wildchild247 on 2007-11-06
will I give eph1973 solution a try?

or are we gonna be doing that after this

---

### Post by meierfra on 2007-11-06
Strange. 

Let's try the same thing from ubuntu (not the Live CD):

cd  /boot/grub
sudo cp menu.lst.external menu.lst   
sudo grub --device-map=device.map
find /boot/grub/menu.lst
root (hd0,0)
setup (hd0)
        (copy the contents of the terminal and post it here)
quit


and reboot with external drive first in the boot order. 
If things go wrong, the same procedure as the last times will get you back into ubuntu

---

### Post by meierfra on 2007-11-06
Try  what I just suggested, after that feel free to try anything  else.  I recommend  trying super grub  before eph1973 solutions (since in my opinions eph1973 solution  has three different mistakes and you won't  get  very far).  Super grub might be able to install grub onto the external hard drive for you.  But Super grub won't be able to edit your "menu.lst". That is not a big deal, If you ever succeed to get to the Grub menu after booting from the external drive, most of your troubles are over and things just need a little tweaking,

Actually  getting Super Grub is a  good idea anyway. I wanted to suggested it at the very beginning but somehow  never did. Super grub will allow you to boot into Windows and into Ubuntu under almost all circumstances.

For information on Super Grub see :[Hermanzone]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by meierfra on 2007-11-06
I think the first paragraph in  eph1973   post is correct. This will allow you to boot into Vista without the external hard drive plugged in. But you won't be able to boot into ubuntu anymore.(unless either we or  super grub succeed to install grub to the mbr of the external hardrive) But since you learned how to reinstall grub you might as well give it a try.
So if you find yourself unable to boot into ubuntu after trying eph1973 method just do  this in the Live CD terminal:

sudo grub
root (hd1,0)
setup (hd0)
quit

---

### Post by wildchild247 on 2007-11-06
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/menu.lst
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

```

I knew what went wrong initially, I left out a part in post #23

here are the contents of the terminal after inputing the code

---

### Post by meierfra on 2007-11-06
That looks exactly like it should. So if you haven't done yet, reboot from the external hard drive and hope for the best,

---

### Post by wildchild247 on 2007-11-06
woo hoo

I put the external HD first on the boot and it gave me the grub option and I was able to boot into windows and ubuntu

---

### Post by meierfra on 2007-11-06
Great! Turn of your computer, unplug the external hard drive, leave the boot order as it is (external first) and then follow eph1973 method to  install the windows boot loader  to the MBR of the internal drive:

> In order to do dual boot with Linux without needing the external hard drive plugged in, you are going to need to blow up the GRUB install on your internal hard drive. This can be achieved by putting in your Vista CD/DVD and booting up with it.
From there, click on "Repair your Computer"
Select your Vista installation, and then click "Next >"
Click on command prompt
At the prompt type
Code:

Bootrec /FixMBR

then type exit.
Remove the Vista CD/DVD from your computer, and reboot

After that you should be all set.

---

### Post by wildchild247 on 2007-11-06
Double woo hoo
windows boots up without the external HDD
I am really pleased at the moment

Thanks for all the help

I really appreciate it

Now I will document this so I have it on my records

Thanks again

---

### Post by meierfra on 2007-11-06
> Thanks again

Your are welcome. Glad to be of help.

---

### Post by eph1973 on 2007-11-08
Just as a note:

The solution that I posted previously is what I did (although since I use XP for my dual boot, I had to look up how to do the same thing in Vista).  It works fine.  I listed in my post that it was my assumption that he had GRUB installed still on his Ubuntu side, and that if that wasn't the case, something else would have to be done.

In any event I good to hear that you are to where you needed to go.

---

### Post by meierfra on 2007-11-11
> since in my opinions eph1973 solution has three different mistakes 

After some testing  I have to  withdraw this statement. One of the things I thought were wrong turn out to be correct (at least on  my computer) and one of them  I should not have counted  as a mistake in the first place.

Just to compare: I had suggested to install grub  to the MBR of the via:
```

cd /boot/grub
sudo gedit  device.map

Change the device.map to:
(hd0) /dev/sdb
(hd1) /dev/sda

sudo grub --device-map=device.map
root (hd0,0)
setup (hd0)
quit

```

This of course worked, but it turns out that one does not need to edit the device.map. 
So  eph1973 method accomplishes the same thing and is much shorter:

```

sudo grub
root (hd1,0)
setup (hd1)
```

---

### Post by lunamystry on 2007-11-11
Hi.

i have two hard drives and i installed gutsy on the one and i play around with the other one installin anything on it. now i would like to remove the second hard drive and be able to control grub from my gutsy installation in the first hard drive.

---

### Post by eph1973 on 2007-11-12
Was your second hard drive the first one your BIOS sought when you booted up, and therefore GRUB was installed on its boot sector?  If you post the output of the following commands from the terminal, we could tell you basically where GRUB currently is:
```

cat /boot/grub/menu.lst
sudo fdisk -l

```

---

### Post by lunamystry on 2007-11-12
well i don't have an internet connection on my pc at the moment. I'm using operamini i'll try to post the things though.

---

### Post by lunamystry on 2007-11-12
I attached the results I hope yall can see them, I am using a windows PC and I forgot to save the file as txt when I made it on my PC. 

```
lunamystry@Mandla1220:~$ cat /boot/grub/menu.lst
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
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

#A splash image for the menu
splashimage=(hd0,0)/boot/grub/splashimages/mac08.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=022719a6-8c40-4cfd-8505-7d491329f24c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
# defoptions=quiet splash vga=792

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
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=022719a6-8c40-4cfd-8505-7d491329f24c ro quiet splash vga=792
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=022719a6-8c40-4cfd-8505-7d491329f24c ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
lunamystry@Mandla1220:~$ 
[sudo] password for lunamystry:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x935bb320

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19273   154810341   83  Linux
/dev/sda2           19274       19457     1477980    5  Extended
/dev/sda5           19274       19457     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d1e4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9545    76670181   83  Linux
/dev/sdb2            9546        9729     1477980    5  Extended
/dev/sdb5            9546        9729     1477948+  82  Linux swap / Solaris

Disk /dev/sdc: 254 MB, 254017536 bytes
16 heads, 32 sectors/track, 969 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00097739

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         969      248013+   6  FAT16
lunamystry@Mandla1220:~$ 


```

---

### Post by eph1973 on 2007-11-12
How do you normally boot into Gusty?  It looks like according to your menu.lst that the only choice you have when you boot up is Gusty.  If you know which of your hard drives your Gusty install is on, if you go to your BIOS and select that one to be the first drive your BIOS checks, you should be able to boot into Gusty without your other drive.  You should then be able to remove the drive you want to.  Probably the best way to handle things based on what you want to do is just to change the boot order from your BIOS rather than using GRUB to select the OS, especially since you want to put whatever you want on the second drive and be able to remove it as necessary.

---

### Post by lunamystry on 2007-11-12
I was about to write that i dnt know what bios is until i pressed del when the computer was switching on. It appears that the hard drive in which gutsy is installed is recognised as a slave and there is no master. 

i installed ubuntu-kde-gutsy on my 80g hard drive with the 160g one connected which is the one with ubuntu-gutsy which is what i dont really want to loose.

---

### Post by eph1973 on 2007-11-12
BIOS stands for basic input output system.  It's part of your motherboard.  Your problem can definitely be solved by changing the boot order of your hard drives.  The problem is, is that everyone's BIOS is a little different.  When you first turn on the computer, in the upper left hand corner of the screen, you should see your BIOS manufacturer and version.  The manufacturer is probably either AMI, Award, or Phoenix.  

Also, since this is a GRUB thread, you would probably find other people that have your specific BIOS setup that may be able to help you better if you start a new thread asking how to set up your BIOS to boot from your second hard drive (it could be as simple as just removing the desired hard drive, to having to play with the settings in your BIOS, and I don't want to tell you anything that will mess you up).  Make sure when you make your new thread, that you include the manufacturer and version of your BIOS, the type of hard drives you wish to keep and remove, and the output of the command sudo fdisk -l in your terminal.  Once you get your BIOS to boot to your 80GB HD first, your GRUB issue should be solved.  Good luck.

---

### Post by lunamystry on 2007-11-13
Okay thank you.

---

