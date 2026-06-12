---
title: "[SOLVED] Reboot"
date: 2008-03-05
forum: General Help
---

### Post by ububaba on 2008-03-05
I am pretty sure this question has been answered earlier. Can't find the solution.
Every time I do a start, I end up on the black screen, asking me to reboot, instead
of starting directly in Gnome interface. Where is the flaw? Thanks for anticipated
help.

---

### Post by pointone on 2008-03-05
Post the exact message you are seeing on the screen, please.

---

### Post by ububaba on 2008-03-05
> **pointone said:**
> Post the exact message you are seeing on the screen, please.
No message pops on the screen. Ubuntu starts loading but half way it stops and 
I end up in the shell at the root level. If I write "reboot" and press "enter" then a 
"normal" process starts, later I can enter name and password in the regular fashion.

---

### Post by pointone on 2008-03-05
> **ububaba said:**
> I end up on the black screen, asking me to reboot...

Sorry, this led me to believe a message was appearing asking you to reboot.

It's logging you in as root, then? Sounds like it may be booting in single user mode. Post the contents of your /boot/grub/menu.lst file, please!

---

### Post by ububaba on 2008-03-05
> **pointone said:**
> Sorry, this led me to believe a message was appearing asking you to reboot.

It's logging you in as root, then? Sounds like it may be booting in single user mode. Post the contents of your /boot/grub/menu.lst file, please!
I should have stated, I am a single user. No one else logs on the machine.

[HTML]
ubu@ubu~$ sudo cat /boot/grub/menu.lst
[sudo] password for clap:
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
timeout         5

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
# kopt=root=UUID=8aec9452-1cf3-4028-9a59-8ce30cd8e375 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8aec9452-1cf3-4028-9a59-8ce30cd8e375 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8aec9452-1cf3-4028-9a59-8ce30cd8e375 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP 2000
root            (hd0,0)
makeactive
chainloader     +1

[/HTML]

---

### Post by ubutufan on 2008-03-05
Your box seems to be a dual boot.
Booting Ubuntu on hd0 at partition 0 and
Booting Windows 2000 on the same partition???????

This is weird.

What system had you had installed first?

---

### Post by DavidTangye on 2008-03-06
> **ububaba said:**
> I should have stated, I am a single user. No one else logs on the machine. This is not what ***pointone*** means when he says[quote=pointone]Sounds like it may be booting in single user mode[/quote]You might be the only person using the machine, so you have set up just one user account for login, but :[LIST=1]
[*]There are another dozen or so 'user' accounts set up to control the machine, including the superuser 'root'.
See them all listed in /etc/passwd. ```
sudo cat /etc/passwd
```One of them is the one you nominated at install time to use for your personal login sessions, ie to a gnome 'desktop' session. You have not and need not define any more such user accounts, as you are the sole user of the system.
[*]'Single user mode' is a special machine startup mode whereby the machine is started with a single terminal made available, and the superuser (root) is logged into it already. This is common to all linux and unix systems. It is used so administrators get complete and sole access to the machine, to recover from drastic problems.[/LIST]I hope this makes it apparent to you, the 'single user mode' is not related to you being the only person who has a desktop account on the machine.

---

### Post by ububaba on 2008-03-07
> **ubutufan said:**
> Your box seems to be a dual boot.
Booting Ubuntu on hd0 at partition 0 and
Booting Windows 2000 on the same partition???????

This is weird.

What system had you had installed first?
I have been messing around a lot which resulted in those oddities. After some attempts, 
finally concluded that the best method was to install on another partition. This took time. 
Till now its smooth sailing. Thanks for all the help.

---

