---
title: "Error 11.  Dual boot problems with XP.  Laptop.  Any help is appreciated."
date: 2007-09-15
forum: General Help
---

### Post by ninjie on 2007-09-15
**_[COLOR="black"][COLOR="Red"]SOLVED  THANKS TO MAESTRO AND LOGOS34!! [/COLOR][/COLOR]_**

First and Foremost.  Im sorry,.... I am a noob.

That being said I have a problem.  Im an expert Windows and Apple user, but im just getting into linux myself and have the ability to understand a new operating system, but I'm still "navigating the fog" as it were.

Windows XP, Dell Inspiron 9300, everything up to date.
        1.  Installed Ubuntu on a seperate Partition of the same 80 gig HD that Windows is on.(10 Gig split =                   8 gig main/2 gig swap)
        2.  Workd fine for eight months as a Dual boot until I updated.

     Today I loaded Ubuntu and started playing around with "APT-GET"  And suddenly, when I reboot, there is no option for me to boot into windows anymore.  Only memtest and the Ubuntu options.

When I select "other operating systems" it says "ERROR 11: Unrecognized device string"


ALL I DID was try the following commands in terminal

apt-get clean
apt-get update and upgrade
apt get autoclean?(is that right?)

I emptied the garbage files.

Now when I boot there is no Windows Option, though the HD on Ubuntu clearly shows all of my windows System Files.

Again, Sorry Im a noob, but is there a way to correct this?  A boot manager or maybe a trick with this "grub" busines?

Im in need of assistance and am Greatful to anyone who can assist or point me in the right direction.

***IM assuming it may be the boot.ini file, but Im not entirely sure if that even factors into this particular problem.***

---

### Post by Maestro23 on 2007-09-15
Can you open a terimnal and type:

> cat /boot/grub/menu.lst (lowecase L)

Copy/Paste the output here.

---

### Post by ninjie on 2007-09-15
Thank you very much for the quick reply.



As Requested.

pilot@uSprocket:~$ cat /boot/grub/men/lst
cat: /boot/grub/men/lst: No such file or directory
pilot@uSprocket:~$ cat /boot/grub/menu/lst
cat: /boot/grub/menu/lst: No such file or directory
pilot@uSprocket:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=0d4fb946-0d57-4fbb-8957-8c5c8b1347c0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0d4fb946-0d57-4fbb-8957-8c5c8b1347c0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=0d4fb946-0d57-4fbb-8957-8c5c8b1347c0 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0d4fb946-0d57-4fbb-8957-8c5c8b1347c0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0d4fb946-0d57-4fbb-8957-8c5c8b1347c0 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

---

### Post by logos34 on 2007-09-15
find your windows partition with 

**sudo fdisk -l **(as in letter L)

If, for example, it's the second partition, then add an entry to bottom of menu.lst like this:

> title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1

---

### Post by ninjie on 2007-09-15
Im doing that now, Ill let you know what happens momentarily.  Thank you so much for the help.

---

### Post by ninjie on 2007-09-15
....I do not know where to find the menu.lst or how to open it for editing.

On my desktop I have two HD.s

Sda1 and sda2

2 is the Partiton with windows on it.


How can I add those lines of code to the menu doc?

---

### Post by ninjie on 2007-09-15
i found it.  Did a search and it came up.  Aplying the changes now.

---

### Post by ninjie on 2007-09-15
When I try to Save the new code in the menu.lst, it tells me I do not have permission to do this?  


Is there some sort of sudo command or am I missing something?

---

### Post by logos34 on 2007-09-15
you must open it as root:

gksudo gedit /boot/grub/menu.lst

---

### Post by ninjie on 2007-09-15
woot.




IT worked!  Thank you so much for the help logos!  Im sure this stuff is the most basic thing for you, but for me it was completely unknown.  Today I learned something and you helped me out of a tight spot.



I am greatfully appreciative.  


-Ninjie
-Trainer and Product consultant
BFG Graphics Technlogies

---

### Post by Maestro23 on 2007-09-15
> **ninjie said:**
> When I try to Save the new code in the menu.lst, it tells me I do not have permission to do this?  


Is there some sort of sudo command or am I missing something?

gksudo (graphical) or sudo (command line)

RootSudo: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

---

### Post by Maestro23 on 2007-09-15
> **ninjie said:**
> woot.




IT worked!  Thank you so much for the help logos!  Im sure this stuff is the most basic thing for you, but for me it was completely unknown.  Today I learned something and you helped me out of a tight spot.



I am greatfully appreciative.  


-Ninjie
-Trainer and Product consultant
BFG Graphics Technlogies

Good deal man.  Can you go back to your 1st post, edit it and mark it SOLVED.

---

### Post by logos34 on 2007-09-15
> **ninjie said:**
> woot.




IT worked!  Thank you so much for the help logos!  Im sure this stuff is the most basic thing for you, but for me it was completely unknown.  Today I learned something and you helped me out of a tight spot.



I am greatfully appreciative.  


-Ninjie
-Trainer and Product consultant
BFG Graphics Technlogies

Glad to hear.  

As for 'navigating the fog', well, I think you're making heavy weather out of it.  ;-)  You'll soon find it rather easy.

---

