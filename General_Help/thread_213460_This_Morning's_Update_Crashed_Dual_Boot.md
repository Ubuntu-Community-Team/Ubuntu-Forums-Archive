---
title: "This Morning's Update Crashed Dual Boot"
date: 2006-07-11
forum: General Help
---

### Post by cssutto on 2006-07-11
This morning's update crashed dual boot.

I have all of my accounting on W2K and today is an important day for me in accounting.

HELP!!

How do I get dual boot back?

Dapper, W2K

I have been so pleased with Dapper.  It works so much better than W2K there is no comparison.  But this morning has been a shock.

CSSJR

---

### Post by klytu on 2006-07-11
> **cssutto said:**
> This morning's update crashed dual boot.

I have all of my accounting on W2K and today is an important day for me in accounting.

HELP!!

How do I get dual boot back?

Dapper, W2K

I have been so pleased with Dapper.  It works so much better than W2K there is no comparison.  But this morning has been a shock.

CSSJR

What boot loader are you using for your dual boot? Can you boot into Ubuntu, still?

---

### Post by nanotube on 2006-07-11
and what is the update that you downloaded, if you remember?

---

### Post by hanzomon4 on 2006-07-11
Was your kernel updated? If so it may have changed your "/boot/grub/menu.list"

I always have to redit mine becase it changes the hard drive it looks into for the linux kernel.

---

### Post by cssutto on 2006-07-11
I am still leearning (funbling) may way around in linux, so there is much I do not know.

Grub is what I think I had.

Interesting.  I just used Debia to go to boot administration and got the error message that there is no /usr/bin/boot-administration.

So apparently some file got zapped.

There is no /boot/grub/menu.list.

There is a config-2.6.15.26-386

CSSJR



CSSJR

---

### Post by cssutto on 2006-07-11
> **nanotube said:**
> and what is the update that you downloaded, if you remember?

An interesting question.

I use package manager for my updates.  I run it a couple of times a day to see if I need updates.

Everything worked fine at midnight last nigt.

This moring, I had a long update, lots of files, and shortly after tht tried to boot W2K.

So I assumed that i was the morning update.

I have 2.6.15.26-386 but whether it was updated this morning or sometime yesterday I can not say.

CSSJR

---

### Post by PriceChild on 2006-07-11
> **cssutto said:**
> There is no /boot/grub/menu.list.

It is /boot/grub/menu.lst (No i in the extension)

---

### Post by cssutto on 2006-07-11
Please pardon all of the typos.

My keyboard was sticking because I had the mouse receiver too close to the back of the machine.

CSSJR

---

### Post by cssutto on 2006-07-11
The joke is on me.

When Dapper added the line for the new kernal, the W2K option in the boot list scrolled off the bottom of the window.

I thought it was gone.

I even scrolled down to the "Other Operating Systems" and clicked on it and paniced when nothing happened.

I just now found out that one more click on the down arrow brings up W2K as a boot option.

So I have practically had an ulcer all day for nothing more than one click on the down arrow.

I feel better already.

Thanks for the help anyway.

CSSJR

---

### Post by hanzomon4 on 2006-07-11
> **cssutto said:**
> Please pardon all of the typos.

My keyboard was sticking because I had the mouse receiver too close to the back of the machine.

CSSJR

My bad (I added the "i" in my post) :oops:

---

### Post by The Noble on 2006-07-11
It sounds like you have a lot of kernels packing you system, You could save yourself space and worry if you deleted you older kernels. I suggest you have 2 kernels at most on your system at a time, one stable, and a new one. 

To get rid of old kernels, go through synaptic(search : Linux) and remove all old kernel images, headers, and restricted moduls (all only for the old kernels you don't want). This will clean your grub as well, so you won't lose that W2K again. ;)

---

### Post by cssutto on 2006-07-11
I have only been in linux for about 60 days now, so I am still learning.

I read up on this subject this evening and plan to use the package manager to remove old kernals tomorrow.

Can't tonight because I am doing a complete system backup, linux W2K, the works, and it is going to run for quite a while.

But the first thing in the morning....

Thanks.

CSSJR

---

### Post by Sale on 2006-07-12
I have the same problem after updating to kernel 2.6.15-26-386:

My menu.lst looks like this (XP entry added by me from the pre-2.6.15-26-386 version of menu.lst):

## ## End Default Options ##

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1

I have two SATA drives, with XP being on Sata channel 1 and Ubuntu on Sata channel 2. Grub is on Sata channel 1, i belive.

---

