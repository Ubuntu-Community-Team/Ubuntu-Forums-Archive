---
title: "Dual boot help!"
date: 2007-01-31
forum: General Help
---

### Post by ACrazyGerman on 2007-01-31
I just finished installing ubuntu and I tried starting up Windows XP and it just sits there loading with out going any where.

---

### Post by pissedoffdude on 2007-01-31
Try rebooting your computer with the windows xp cd in the cd drive.  Then go to the recovery mode and sign into your windows xp installation.  Then type in the command "FIXBOOT" (no quotations) and reboot.  Hope that helps.

---

### Post by ACrazyGerman on 2007-01-31
That didn't help. I choose to Load

"Windows NT/2000/XP (loader)"

After I click it, it just sits there doing nothing saying

"Starting up..."

---

### Post by pissedoffdude on 2007-01-31
> **ACrazyGerman said:**
> That didn't help. I choose to Load

"Windows NT/2000/XP (loader)"

After I click it, it just sits there doing nothing saying

"Starting up..."
Go into a terminal and type the command ```
gksudo gedit /boot/grub/menu.lst
``` fidn where it says other operating systems and where it says windows nt/2000/xp.  Then post the output of that

---

### Post by ACrazyGerman on 2007-01-31
New to linux whats the terminal

---

### Post by oracle5 on 2007-01-31
You could try the system rescue cd or gparted cd or even gparted in ubuntu to set the windows partition to the active partition. Thats how I fixed it when I first dual booted.

oracle5

---

### Post by pissedoffdude on 2007-01-31
> **ACrazyGerman said:**
> New to linux whats the terminal

Go to accessories then select terminal

---

### Post by ACrazyGerman on 2007-01-31
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
# kopt=root=UUID=8bcf9b99-9d4f-4583-8d3e-a513550d01ba ro
# kopt_2_6=root=/dev/hda2 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by pissedoffdude on 2007-01-31
Open up your grub menu.lost again and at the bottom where it says title Windows NT/2000/XP (loader) change root to rootnoverify

---

### Post by ACrazyGerman on 2007-01-31
can you please re frase that I am great with windows but linux frankly scares the **** out of me

---

### Post by pissedoffdude on 2007-01-31
Open up the terminal and type the command ```
gksudo gedit /boot/grub/menu.lst
``` Now scroll down to where it says ```
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

``` and change the word root to rootnoverify

---

### Post by ACrazyGerman on 2007-01-31
did that and theres no change windows wont boot up

---

### Post by ACrazyGerman on 2007-01-31
> **oracle5 said:**
> You could try the system rescue cd or gparted cd or even gparted in ubuntu to set the windows partition to the active partition. Thats how I fixed it when I first dual booted.

oracle5

Can you give me detailed instructions to do this?

---

### Post by oracle5 on 2007-01-31
Assuming that you can boot into ubuntu you can type

sudo apt-get install gparted

in the terminal and then go to system>administration>gnome partition editor. 

Right click on your windows partition and click manage flags. Check the boot check box and click ok.

You might have to also click apply but I'm not sure since I'm not able to do it right now.

oracle5

---

### Post by ACrazyGerman on 2007-02-01
when I right click on the part that has windows it shows a warning

"Unable to read the contents of this file system!
Because of this some operations maybe unavailable.
 Did you install the correct plugin for this file system?"

---

### Post by ACrazyGerman on 2007-02-01
any one got any ideas please

---

### Post by ACrazyGerman on 2007-02-01
any one at all?

---

### Post by lswb on 2007-02-01
Before you try any of the more technical fixes already posted, make sure you try rebooting from a complete power-off shut down. I don't know why, but I've seen more than one system that will not boot Windows XP from a "restart" form Linux, but will boot OK if the system is completely powered off before rebooting.

Good Luck!

---

### Post by ACrazyGerman on 2007-02-01
already did that many times.

---

### Post by ACrazyGerman on 2007-02-01
Can any one tell me how to unistall linux and get Windows running by its self again?

---

### Post by SMPS on 2007-02-01
LOL, I have the opposite problem on my home dual boot box (but nowhere else ?!).  I am going to try some similar actions to get Ubuntu to boot and bypass a direct windows boot (which sucks!!!)

Phil

---

### Post by jesus5511 on 2007-02-01
I Have this EXACT same problem, but by trying to fix it I've most likely completely screwed it, word of advice- don't do anything unless your 100% COMPLETELY sure you know what's going to happen if your new to this.

---

### Post by ACrazyGerman on 2007-02-01
Yeah its pissing me off i can't get to any of my files at all to even back them up. And I got some work I got to do but I can't get to it because of this its pissing me off so much.

---

### Post by scrooge_74 on 2007-02-01
You need yo use your Windows CD and start in recovery mode so it can rewrite to boot loader

---

### Post by ACrazyGerman on 2007-02-01
> **pissedoffdude said:**
> Try rebooting your computer with the windows xp cd in the cd drive.  Then go to the recovery mode and sign into your windows xp installation.  Then type in the command "FIXBOOT" (no quotations) and reboot.  Hope that helps.

You mean that?

Cause it doesn't work.

---

### Post by jesus5511 on 2007-02-01
I actually tried doing the fixmbr thing, and it totaly screwed up my computer, when I started it it just brought up a disk read error, but luckily I was able to reinstall ubuntu through the disk.

---

### Post by jesus5511 on 2007-02-01
Is their anymore possible solutions for this at all?

---

### Post by ACrazyGerman on 2007-02-01
I hope so or I have to reformat my whole computer and reinstall every thing. Does any one know any way to get to the other half of my computer with windows on it so I can at least back stuff up?

---

### Post by jesus5511 on 2007-02-01
I tried using the super grub disk, I messed around with it for a bit tryiing to think of all the possible ways I could fix it, I'm not going to go through all of them, but when I tried using the boot windows partition command it said "NTLRD" is missing (or however you spell it, I've fogotten it by now,) so I look on google and found some stuff and went into the XP recovery console and did fixboot, it said the sectors were corrupt and that it repaired them, but windows still refuses to start (although it no longer gives me the missing/invalid error.)

I've been trying to fix this all day and just cannot find any explination or reasoning for this not working..

I don't know if this is anything important, but my boot.ini in the hda1 drive reads:

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS


However I can't seem to get the normal windows booting screen to work, I've done just about everything I can think of, I guess re-installing windows is all thats left.

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

---

### Post by jerrykenny on 2007-02-01
Crazy, if you are very worried about the data on your Windows drive . . . . 

boot into ubuntu

open a terminal . . . .

<sudo apt-get install ntfsprogs>

This will install necessary libs to allow you to open your ntfs partition, . . . personally I've never had to use it, however, I would imagine you would do something like . . .

<sudo mkdir /mnt/windows2000
<sudo ntfsmount /dev/hda1 /mnt/windows2000>

Then use the file browser, point it to,   /mnt/  then /windows2000/  hopefully the data should be there and you can burn it to disk.

(like I said, not too sure about ntfsprogs . . . . but for some help, try typing in a terminal    <man ntfsprogs>   or <man ntfsmount>  )



Good Luck

---

### Post by jerrykenny on 2007-02-01
Alternately, download a copy of "knoppix" from here

[http://www.knoppix.org/](http://www.knoppix.org/)

And boot into it,  its excellent for exploring windows partitions.

---

### Post by ACrazyGerman on 2007-02-02
> **jerrykenny said:**
> Alternately, download a copy of "knoppix" from here

[http://www.knoppix.org/](http://www.knoppix.org/)

And boot into it,  its excellent for exploring windows partitions.

Can any one give step by step instructions i don't know what one to download or how to install it

---

### Post by scrooge_74 on 2007-02-02
You need to go to the site, click on download and pick a server to download the iso image, after you need to burn that iso image to a CD and then you can boot from said CD

The iso file to download has a name like KNOPPIX_V5.1.1CD-2007-01-04-EN.iso

---

### Post by helliewm on 2007-02-02
See my very depressing thread. Bigken had to use specialist data recovery discs to retrieve my sister's files.

[http://www.ubuntuforums.org/showthread.php?t=339101&highlight=stuck+installation](http://www.ubuntuforums.org/showthread.php?t=339101&highlight=stuck+installation)

Helen

---

### Post by ACrazyGerman on 2007-02-02
I have my most important files on my flash drive now. Is there any easy way to unistall linux and put my harddrive back together and be able just to use windows again?

---

### Post by scrooge_74 on 2007-02-02
Use your windows CD repartition the drive again so you can reinstall XP

---

### Post by ACrazyGerman on 2007-02-02
Do you think reinstalling over it will work just fine so I don't lose any thing or should I totaly format it all and start a new?

---

### Post by scrooge_74 on 2007-02-04
Supposedly you could use the master boot restore from the CD.  But I dont have that much expirience doing that I always reformated everything

---

