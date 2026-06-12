---
title: "Installed Grub to Windows Partition. How i can recover?"
date: 2007-02-06
forum: General Help
---

### Post by AkumA on 2007-02-06
Hi, after a long evening passed on setup few things i've done the best thing in the world:

```
grub-install hda
``` instead of ```
grub-install hd0
```

I've grub installed in the MBR but for some reason i've typed hda and now i can't load windows.

How can i recover?
I've tryed to boot a LiveCD (Ubuntu 6.06) and i saw that the partition is "Bootable" and i can't remeber if it's right because it's the first partition or what. I need to rest because there's another 6 hour night for me.. 

I've Ubuntu Edgy 6.10

hda1 is WinXp
hda2 is root for Ubuntu Edgy
hdb1 is NTFS music/films bla bla
hdb2 is root for Slackware
hdb3 is home for both Ubuntu&Slackware
hdb4 is spam

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
# kopt=root=UUID=c95cd549-45ec-4cfb-bb79-96030521b226 ro
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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

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

title           WindowsXP        
root            (hd0,0)
#savedefault
makeactive
chainloader     +1


title		Slackware-11.0
root		(hd1,1)
kernel          /boot/vmlinuz-2.4.33.3 root=/dev/hdb2 ro
initrd          /boot/initrd.img-2.4.33.3
quiet
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Thank you

---

### Post by r4ik on 2007-02-06
try,

[http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655)

Good luck !

---

### Post by AkumA on 2007-02-07
I see... but i've started Ubuntu 6.06 Live CD and when it comes the partition manager there's the NTFS WinXP partition with the "Bootflag" and it's not mounted correctly. In my Edgy there's  hda1 in /media/hda1 but it's not mounted.
After a good night (Yeahh, nightmares too! hauhau!), i realized that maybe grub, even if i don't know very well how it works, has flagged or mounted as "Boot" the /media/hda1.
So i think i can go somewhere or do something to re-mount the /media/hda1.

A friend suggested to boot WinXP installer CD and fix boot from there. Then, i think, i could re-install Grub in the MBR targeting hd0 with ```
grub-install hd0
``` i suppose.

BTW ..i don't remember winxp installation at all.. :D ..but i remember slackware very well.. i think this is positive :D

---

### Post by AkumA on 2007-02-07
Oh i forgot! When i run cfdisk i see the flag bootable and
```
[]
```
under the column "Label".

But tonight i couldn't find a way to remove or change that!

---

### Post by AkumA on 2007-02-07
I've found the answer!

I'll test it in few minutes.
I'm sorry for the posts.. but i've tried in google for a day and half to find something about my problem and only today i've found the thread in this forum.

[http://ubuntuforums.org/showthread.php?p=2119274#post2119274](http://ubuntuforums.org/showthread.php?p=2119274#post2119274)

---

