---
title: "[SOLVED] Error 17"
date: 2007-11-13
forum: General Help
---

### Post by Poupaa on 2007-11-13
Everything seems to run allright : Ubuntu installs well, but by rebooting, I get each time this message :

> find --set root --ignore-floppies /ubuntu/install/boot/grub/menu.lst

Error 17 : File not found

Press any key to continue...

I'm using Wubi 7.10-386 and either Ubuntu desktop-i386 or Ubuntu -desktop-amd64 
I did this a number of times, changing Wubi version or .iso version, it's always the same.
Please, I really do WANT to get Ubuntu installed and give it a try

---

### Post by ago on 2007-11-13
This is 7.10 I assume. Do you get that soon after rebooting from windows or after second rebooting (after the chocolate fudge screens).

Do you see /ubuntu/install/boot/grub/menu.lst

---

### Post by Poupaa on 2007-11-13
Ubutu installs and the machine reboots. Then from the boot menu I choose Ubuntu-Linux, and this is there yhat I get tis message
Yes I can see the file you mention, and Yes, I use Ubuntu 7.10.isi

---

### Post by ago on 2007-11-13
Try to run chkdsk /r on the partition on which where you installed wubi
Also you can press esc on the countdown, then hit "c"

Then type

configfile (hd

then hit tab to autocomplete/show available options, keep navigating using the tab key and see where you stop.

---

### Post by Poupaa on 2007-11-13
Sorry for taking so much time

chkdsk /r made

I rebooted and pressed esc. I got this message :

> GRUB4DOS 0.4.3 2007-10-21, Memory : 627K / 2046M , CodeEnd 0x41538
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere eslse TAB lists the possible completions of a device / filename ]

grub> -


I typed what you said :

grub> configfile (    and hit TAB. It gave me the choice betwenn hd0 and hd1. I typed hd0, which corresponds to my Windows C disk where Wubi is located. Then I hit TAB again, I got following message :

> grub> configfile (hd0,
          Possible partitions are :
           Partition num : 0, Filesystem is ntfs, partition type 0x7
           Partition num : 4, Filesystem is ntfs, partition type 0x7

and that's all. can you do sthg for me with these info ?
Thank you Ago

---

### Post by ago on 2007-11-13
that's the list of your options
type either 0 or 4 then hit tab again
and so on until you browse to the menu.lst file

---

### Post by Poupaa on 2007-11-13
My next step :
 
 grub> configfile (hd0,0)

When I hit TAB then, :

  Error 1 : File name must be either an absolute pathname or blocklist

Other options give absolutely no response

Hope you can continue helping me to go further.

---

### Post by ago on 2007-11-15
the path should be

configfile (hd0,0)/ubuntu/install/boot/grub/menu.lst

or 

configfile (hd0,4)/ubuntu/install/boot/grub/menu.lst

you can press tab along the way to see if you are on the right track

---

### Post by Poupaa on 2007-11-15
The path : configfile (hd0,0)/ubuntu/install/boot/grub/     worked fine, but then when I hit TAB : 'Error 1' !
I typed then : configfile (hd0,0)/ubuntu/install/boot/grub/menu.lst, and I got : 'Error 17, file not found'

So I booted into Windows and gave a look to my folder 'C:\ubuntu\install\boot\grub' and then,the file 'menu.lst you told me to look for, and that was there some time ago had 'disappeared'.
I swear I'm not Harry Potter and I didn't delete any file.
Can you figure what happens ?
What shoud I do ? reinstall the whole thing ? I'm really puzzeld !

I did 'chkdsk /r, but nothing !

---

### Post by ago on 2007-11-15
The file gets deleted at the end of the installation since it contains your password. That would indicate that the installation succeeded. You should then try to boot off 

/ubuntu/disks/boot/grub/menu.lst

---

### Post by Poupaa on 2007-11-15
I type 'configfile (hd0,0)/ubuntu/disks/boot/grub/menu.lst'  ENTER
and I get this : 
> GRUB4DOS 0.4.3 2007-10-21, Memory : 627K / 2046M , CodeEnd 0x41538
[Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere eslse TAB lists the possible completions of a device / filename ]

grub> -

---

### Post by tech9 on 2007-11-15
> **Poupaa said:**
> Everything seems to run allright : Ubuntu installs well, but by rebooting, I get each time this message :



I'm using Wubi 7.10-386 and either Ubuntu desktop-i386 or Ubuntu -desktop-amd64 
I did this a number of times, changing Wubi version or .iso version, it's always the same.
Please, I really do WANT to get Ubuntu installed and give it a try

supergrub
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by ago on 2007-11-15
is the file visible when using the following? What is the content of menu.lst?

configfile (hd0,0)/ubuntu/disks/boot/grub/[TAB]

---

### Post by Poupaa on 2007-11-15
tech9 : ty, I'll give this a try if Ago's solutions don't succeed.

Ago :
Yes, the file is visible
Content of the file : 
> # menu.lst - See: grub(8), info grub, update-grub(8)
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

## timeout 3
# Set a timeout 3
# (normally the first entry defined).
timeout 3

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
# kopt=root=UUID=F6E4B856E4B81B37 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)/ubuntu/disks

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
find		--set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
kernel		/ubuntu/disks/boot/vmlinuz-2.6.22-14-generic root=UUID=F6E4B856E4B81B37 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/ubuntu/disks/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
find		--set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.d
ü¶úl8áB®LÁ£ŽÔž4AÕÇJÇbëÞ…Ê-=1a`Wx“êNjÅÂüñ„	±¶²8£çØÒÄô

---

### Post by ago on 2007-11-15
The file is corrupted, as you can see from the gibberish at the bottom
Simply deleting that trash should do the trick

But if that is corrupted other files might be corrupted as well... So you migt have to reinstall. Have a go anyway.

---

### Post by Poupaa on 2007-11-15
I deleted the strange things at the bottom of the file, but it didn't work either.
So I reinstalled 3 or 4 times, ran chkdsk /r , but each time, the /unbuntu/disks/boot/grub folder is empty. I miss the menu.lst file.
I begin to get a little bit desperate.

---

