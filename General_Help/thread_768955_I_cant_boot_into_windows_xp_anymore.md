---
title: "I cant boot into windows xp anymore"
date: 2008-04-26
forum: General Help
---

### Post by wobleboble on 2008-04-26
Hi,

Im new to ubuntu, always been using windows xp untill i started hearing how ubuntu is better etc. So i have just downloaded the ubuntu hardy heron.

I have 2 hard drives, 80gb and 250gb.  I am using the 250gb for my windows xp and the 80gb was connected but not doing anything, just sitting there. So i have installed ubuntu onto the 80gb hard drive. Now whenever i boot up my pc i dont get any options at all to boot up into my windows xp :(   

When i boot into ubuntu i can access the 250gb hard drive and go threw all the files but i want to actually boot into the windows xp and use the applications ie to play games that i have got on it.

How can i get the option to boot into windows xp or ubuntu when i start the pc up??

thanks

---

### Post by TeoBigusGeekus on 2008-04-26
You haven't installed grub, have you?
Go to this page, read the documentation, download super grub, burn it on a cd and boot with it...
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by wobleboble on 2008-04-26
Hi, thanks for the quick reply.  I have been reading a bit about and this given it a shot but im stuck and cant find the solution.  I have got grub on a cd and have restarted my pc. When it comes up with booting from cd it says something liek booting/starting grub but then it just goes to ubuntu loading screen.  Am i missing something?

I downloaded supergrubdisk_0.9677.iso
Is that the correct iso for my situation?

---

### Post by TeoBigusGeekus on 2008-04-26
Wait, wait, wait...
Do you mean that whenever you start your pc you see grub loading?
If so, press the esc button and you will see a menu in which you can choose which os you want to boot.

If not, then the iso you downloaded should be ok. Burn it and boot with it. Read the documentation on supergrub site on what to do next.

---

### Post by wobleboble on 2008-04-26
Oh sorry i mean when i start my pc i dont see anything about grub or windows, it automatically goes to ubuntu but when i put the grub iso onto a cd and restarted the pc, it did say at the bottom of the screen something like grub loading.... but then it doesnt do anything except load up ubuntu.  

When i read the documentation on supergrub website it shows me screencaps of supergrub and what to do next etc but i am not able to get to the first screen of grub.  It doesnt show up at all when i reboot the pc with the cd in, it only says something like loading grub.... and then it dissapears after 5seconds and then i see ubuntu loading screen.

---

### Post by TeoBigusGeekus on 2008-04-26
While grub is loading, did you try to press the esc button?

---

### Post by the8thstar on 2008-04-26
please type 

> sudo fdisk -l

in the terminal and paste your results in your next post.

---

### Post by wobleboble on 2008-04-26
yes i pressed esc and it gives me these choices -

ubuntu 8.04 kernel 2.6.24-16-generic
ubuntu 8.04 kernel 2.6.24-16-generic (recovery mode)
ubuntu 8.04 memtest86+



this is what has come up in the terminal

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5ebd54c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xede6b08c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30400   244187968+   7  HPFS/NTFS

---

### Post by the8thstar on 2008-04-26
Thank you.

Now type:

> sudo gedit /boot/grub/menu.lst

and paste the results here. This way, we can see what Grub is supposed to do and we can go from there.

---

### Post by wobleboble on 2008-04-26
ok thanks, here is the results - 


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
timeout		3

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
# kopt=root=UUID=2b7c049a-fcbf-4632-888f-30313c4f9660 ro

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2b7c049a-fcbf-4632-888f-30313c4f9660 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2b7c049a-fcbf-4632-888f-30313c4f9660 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by wobleboble on 2008-04-26
smiley faces have come up lol its meant to be   ( 8 ) without the spaces where the smiley faces are

---

### Post by zvacet on 2008-04-26
```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
```

```
gksudo gedit /boot/grub/menu.lst
```


Under this line 
### END DEBIAN AUTOMAGIC KERNELS LIST

title                     Windows
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

sava file and close it.Reboot and you should be able to boot in windows.

---

### Post by wobleboble on 2008-04-26
When i restarted the pc it did give me the option for Windows in the list, when i selected it i receive this message on the screen - 

Starting up...

NTLDR is missing
Press CTRL+ALT+DEL to restart

---

### Post by the8thstar on 2008-04-26
Check this link:

[http://www.tinyempire.com/notes/ntldrismissing.htm]("http://www.tinyempire.com/notes/ntldrismissing.htm")

It might contain the solution you need. Keep us updated.

---

