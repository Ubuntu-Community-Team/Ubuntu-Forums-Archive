---
title: "Video mode not supported"
date: 2007-09-25
forum: General Help
---

### Post by yyz on 2007-09-25
Hello, I have installed on my PC a Xubuntu OS. I've been having this problem for a while now, and I couldn't figure how to solve it on my own.

At booting my computer I get an error message "Video mode not supported". 
How may I stop it from being displayed, since its a drawback/delay for the system?

---

### Post by yyz on 2007-09-26
Bump

---

### Post by yyz on 2007-09-26
Bump.

---

### Post by kellemes on 2007-09-26
What videocard do you have?
And did you install a driver for it?

---

### Post by rsambuca on 2007-09-26
You probably have set the incorrect vga mode in your boot options.  If you post your /boot/grub/menu.lst file, perhaps we can see.

---

### Post by yyz on 2007-09-26
> **kellemes said:**
> What videocard do you have?
And did you install a driver for it?

SiS. I didn't install a driver for it.

> **rsambuca said:**
> You probably have set the incorrect vga mode in your boot options.  If you post your /boot/grub/menu.lst file, perhaps we can see.

Here is the menu.lst file:

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
# kopt=root=UUID=604d5d46-7954-4829-b0fc-5762f9301637 ro
# kopt_2_6=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.17-12-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-12-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-12-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by rsambuca on 2007-09-26
menu.lst looks OK to me.  Sorry, guess that wasn't it.

---

### Post by kellemes on 2007-09-26
> **rsambuca said:**
> menu.lst looks OK to me.  Sorry, guess that wasn't it.

Good thought anyway..

I wonder.. at what moment do you get this message?
Is this right after making a selection in the bootmenu? Or is it sometime later?

---

### Post by yyz on 2007-09-26
> **kellemes said:**
> Good thought anyway..

I wonder.. at what moment do you get this message?
Is this right after making a selection in the bootmenu? Or is it sometime later?

When I power-on my computer; as the system loads. (I don't make any selections since I am not dual-booting - I have a single OS installed, and that's Xubuntu 6.06.

---

### Post by yyz on 2007-09-27
Bump

---

### Post by yyz on 2007-09-28
Hello again. I still haven't managed to fix it. Well being honest, I didn't look for a solution.

I'm hoping someone here knows how I could fix this.
Has anyone had a similar problem regarding the error message 'video mode not supported'?

Thank you.

---

### Post by marshmelbo on 2007-09-30
All is fine till I enable the nvidia proprietary drivers, Then on reboot my screen says Mode not supported. Tried all sorts, but to no avail.

---

### Post by yyz on 2007-10-06
bump

---

### Post by yyz on 2007-10-10
bump

---

### Post by Rui Pais on 2007-10-10
Hi,
try to add **vga=ask** to the kernel line of grub. Like this:
```
kernel     /boot/vmlinuz-2.6.17-12-generic root=/dev/hda1 ro quiet splash vga=ask
```

That way it will show a list of available/possible modes, pick the one prefer and change ask for vga=*number_code*

Another ways would be simply try to put a common mode, like:
```
vga=791
```
for 1024x768, or:
```
vga=794
``` for 1280x1024, and see if any of those works.

hth

---

### Post by yyz on 2007-10-24
Hi
Rui Pais it didn't work sorry..

---

### Post by johnny9794 on 2007-10-24
I had same problem.

[http://ubuntuforums.org/showthread.php?t=531247](http://ubuntuforums.org/showthread.php?t=531247)

But i was able to solve it by picking vesa driver for my card so for your SiS, 

> **tseliot said:**
> If you tried the livecd and you was not able to install Ubuntu even when using the Safe Mode:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu (select it using your keyboard) almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "SiS" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

On next reboot the Xserver should work fine



If nothing works and the Xserver just crashes, please post the output of the following command:
```
lspci
```

So apon reconfigure, manually set video card driver and pick SiS.

If and when u find the correct driver selection for your card this will work.

After a year and a half trying to fix the same problem u have that I use to have, was fixed within minutes :).

---

### Post by yyz on 2007-11-03
Nope that doesn't work either. There is still a problem.

---

### Post by minus198 on 2007-11-03
If you have 6.06, you should really really think about upgrading to 7.10 or something. 6.06 is quite old..

---

### Post by yyz on 2007-11-03
Hello minus198, it even says on my profile that I am a Ubuntu Gutsy Gibbon 7.10 user :) Perhaps you were joking when you said that.

Does anybody have any suggestions on this issue?

---

### Post by drtvasudevan on 2007-11-13
[http://ubuntuforums.org/showthread.php?t=579684&highlight=1280x1024+splash](http://ubuntuforums.org/showthread.php?t=579684&highlight=1280x1024+splash)

---

