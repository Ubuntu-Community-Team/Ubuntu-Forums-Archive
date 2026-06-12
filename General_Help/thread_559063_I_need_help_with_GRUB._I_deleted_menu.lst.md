---
title: "I need help with GRUB. I deleted menu.lst"
date: 2007-09-24
forum: General Help
---

### Post by Phayder92889 on 2007-09-24
mmkay. I was tooling around on my box, having fixed something along the line to the point where it wasn't freezing except once every week or so. Not bad, but I'd like it to be rock-solid and never off.

In a fight with my mom, she violently disconnected my box from all my peripherals, and didn't shut me down right.

I don't know what did it, but when I turned it back on, one of the monitors wasn't quite right in the dual-screen-ness, and I restored a backup copy of my xorg.conf over the top of it.

All of a sudden, the freezes came back with a vengeance. In a dead-run panic, I used ELinks through the recovery terminal to get to the page that detailed what to fix in your menu.lst for boot options that (If memory served) greatly assisted my plight.

I open up nano, tell it to navigate to /boot/grub and I thought I'd told it to Open menu.lst.

Nope

I'd blanked it.

So I rebooted, not knowing the dumbness of this move.

Then I was faced with the grub terminal, so I connected through my Lifedrive to search for an answer.

I think (think is the operative phrase, here) I fixed it by using a LiveCD, creating a symbolic link between my install on my hard drive and the /boot/ directory of the LiveCD, then running ```
 sudo update-grub 
```

It printed off a few lines that gave me hope, but I haven't rebooted yet.

Is there anything else I should do before I cycle power and pray?

EDIT: Here's a copy of my menu.lst file. I'm not 100% sure that it'll work, so I'd like to see if someone out there can tell me if I'm good to go or not

```
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
# kopt=root=unionfs ro
# kopt_2_6=root=/home/ubuntu/unionfs ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/home/ubuntu/unionfs ro quiet splash noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/home/ubuntu/unionfs ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/home/ubuntu/unionfs ro quiet splash
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/home/ubuntu/unionfs ro single

title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/home/ubuntu/unionfs ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/home/ubuntu/unionfs ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/home/ubuntu/unionfs ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/home/ubuntu/unionfs ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/home/ubuntu/unionfs ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/home/ubuntu/unionfs ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST 
```

---

### Post by Shazaam on 2007-09-24
Using the live cd and mounting your drive is there a usable backup version of menu.lst hiding in /boot/grub? You could try looking in /root/.trash too. If you find a workable version you could copy it back inside  /grub.

For the future you might consider checking out SuperGrubDisk or SystemRescueCd.

---

### Post by Phayder92889 on 2007-09-24
just checked both, neither turned up anything.

I'm not 100% that the unionfs part is gonna work, that's all.

---

### Post by Shazaam on 2007-09-24
Try this page...
[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

### Post by jamesjtucker on 2007-09-24
1) boot from live cd
2) mkdir /media/drive/
3) sudo mount /dev/[yourdrive] /media/drive
4) sudo chroot /media/drive su
5) update-grub
6) reboot.
:)

---

### Post by Phayder92889 on 2007-09-24
ACK!

I think I'm even more screwed than before.

I didn't know what jamestucker's commands did, but I did them. It seemed fine, up until I looked into the /boot/ directory on Nautilus. I was confused. I rm -rf'd the grub folder on my actual drive thinking I'd be removing the symlink on my livecd part.

...In fact, I know I'm more screwed than before. Can somebody please beat me soundly and tell me how to unf*ck my system?

I return with a grub error 15 on reboot

---

### Post by Adramelech on 2007-09-24
lol!!!

All I can think of, is to boot on live cd, then open synaptic, change root directory using chroot and then install ubuntu-desktop again. havent tried this, but maybe it works

---

### Post by Shazaam on 2007-09-24
Or you can rerun the code that jamesjtucker gave you.

---

### Post by Adramelech on 2007-09-24
update-grub only regenerates the menu.lst file, if the whole directory is gone, is not going to help

---

### Post by Phayder92889 on 2007-09-24
so... How boned am I? Is this one of those "you're so dead that 'dead' doesn't begin to cover the dead-ness that you are experiencing" moments?

Or can I fandangle something back into place and pray that it works for a while?

...please? I like my setup, and It'd suck hardcore to have to go back to nothing.

---

### Post by Adramelech on 2007-09-24
is basically what jamesjtucker said, basically you login as root with your live cd, then you mount your drive so you can write into it, then you change the root directory to get the changes saved into disk, and finally you fix the system.

1) boot from live cd         
2) mkdir /media/drive/                (crate the folder to mount your drive)
3) sudo mount /dev/[yourdrive] /media/drive     (mount your drive)
4) sudo chroot /media/drive su                          (change root directory to get changes on disk and not on livecd)
5) sudo apt-get --reinstall grub                          (reinstall grub)
6) reboot

---

### Post by Phayder92889 on 2007-09-24
Thanks. I'm in the process of reinstalling now. I'll let you know if I manage to get it all made right again.

---

### Post by Phayder92889 on 2007-09-24
I still get an Error 15.

Back on the LiveCD

---

### Post by Adramelech on 2007-09-24
15 : "Error while parsing number"

Do you have a menu.lst file now? is your grub directory with files?

---

### Post by Phayder92889 on 2007-09-24
```
ubuntu@ubuntu:~$ ls /media/disk/boot/grub
device.map  menu.lst  menu.lst~ 
```

that's what's there. I'm working on getting the standard architecture liveCD so I can work better.

---

### Post by Adramelech on 2007-09-25
did some research and erro 15 is not file found.
Grub fails before of after displaying the menu? Have you tried to boot manually?

---

### Post by crazybilly on 2007-09-25
looks like you've got a  menu.lst and a backup...what are the contents of those?

---

### Post by Phayder92889 on 2007-09-25
Grub fails before hitting a menu, both menu.lst files are identical, and I have no idea how to manually boot.

---

### Post by Phayder92889 on 2007-09-25
Alright. I'm moving back to standard architecture now. I'm on the AMD x64 version, and that may be part of the problem. I'm burning the disc now.

To clarify: Both the backup and the menu.lst file present in the boot directory of my hard disk look like this:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
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
# kopt=root=UUID=8568e485-53c0-4013-92bb-8fab76d3db7e ro
# kopt_2_6=root=/dev/hda1 ro

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro quiet splash noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda1 ro single noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro quiet splash noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.17-12-generic
savedefault

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro single noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single noapic nolapic irqpoll ht=on
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Phayder92889 on 2007-09-25
(shameless bump)

I have no idea what to do. Every time I edit device.map to include the right HDD, it refuses to keep my edits.

---

### Post by Adramelech on 2007-09-25
hummm the error 15 you got is becasuse of the stage 1 and 2 got deleted by your rm command, try installing grub again, not from synaptic, but from source code to be honest thats the way o fixed my system some months ago, If you need help with this pm me

---

### Post by Patness on 2007-10-03
I tried the commands listed but I can't get permissions to chroot, whether from sudo or in su.

---

