---
title: "update-grub not running after kernel version upated"
date: 2015-04-22
forum: General Help
---

### Post by davehk on 2015-04-22
Hi,

During the investigation of a problem with aptlib (Thread #2273858, now solved) we discovered that since I upgraded from 10.04LTS to 12.04LTS, update-grub has not been running after update-manager did a kernel update, and that my system was running the original kernel 3.2.0-39 from Feb 2013, even though all the later kernels are present in /boot.

I have edited /boot/grub/menu.lst  (I am still running GRUB, not GRUB2) and added entries for the latest kernel and changed the default entry to point to that, and the system is running fine (actually seems a bit quicker) on the latest kernel. Whilst editing menu.lst I also noticed that update-grub was set not to change the default:

# updatedefaultentry=false

I'd like to fix the update-grub issue so that the latest kernel is booted after an update. Editing the menu.lst entry above is easy, of course, but how do I get update-grub to run after a new kernel is released and installed?

Should I just upgrade to GRUB2? If so, what's the best (i.e. safest) way to do that?

Thanks,

Dave

---

### Post by dino99 on 2015-04-22
grub1 & grub2 does not work together. Ubuntu install now grub2, which is way different.
you'd better to purge grub* & menu.list, and then install grub-pc to /dev/sda  (sudo grub-install /dev/sda)

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by davehk on 2015-04-22
Thanks - yes, knew that and had seen the instructions. Question is will that fix the fact that update-grub is not running after new kernel version is installed?

---

### Post by matt_symes on 2015-04-22
Hi

Just to be on the safe side, make sure you have a bootable CD/USB handy just in case there are any issues before migrating from grub to grub2.

That way any problems can be fixed with a chroot.

I assume your computer's BIOS is not UEFI ?

Kind regards

---

### Post by davehk on 2015-04-22
I have the live CD for 12.04. (and 10.04 and 8.04) as even though I upgraded  LTS>LTS>LTS I always burn myself a Live-CD just in case!

BIOS is non UEFI.

---

### Post by matt_symes on 2015-04-22
Hi

> I have the live CD for 12.04. (and 10.04 and 8.04) as even though I  upgraded  LTS>LTS>LTS I always burn myself a Live-CD just in case!

Excellent. You're all set for grub2 then.

Post back with any problems as there are a whole bunch of people here who can help you.

I'm out for the day.

Kind regards

---

### Post by davehk on 2015-04-30
OK, I've not upgraded to GRUB2 yet - I thought I'd wait for another kernel update and see what happened. So this morning Update Manager found and installed 3.2.0-82 and 3.2.0-82-pae and I opened the detail window and watched. update-grub does run, and it finds all the kernels, and then goes on to update menu.lst - except it doesn't make any changes to menu.lst. The fact that update-grub does run leads me to believe that upgrading to GRUB 2 will fix the problem - but I'd still like to understand why GRUB 1 is not working as it should.

defaults options in menu.lst are:

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
# kopt=root=UUID=195b0fde-6111-4c0f-931e-005965a38c34 ro

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

```

---

### Post by mörgæs on 2015-05-01
If you have Grub1 then you are likely to have the hard disk formatted with ext3, which hardly has any advantages compared to ext4. 

A fresh install of 14.04.2 LTS (maybe using X/Lubuntu if we are dealing with old hardware) will get rid of 12.04, ext3 and Grub1 in one go.

---

### Post by davehk on 2015-05-04
Yes, I'm planning to move to 14.04 on a new HDD later this year but don't have time at the moment to get it all set up and then move all my data, emails, website  etc. across.

---

### Post by matt_symes on 2015-05-04
Hi

> **mörgæs said:**
> If you have Grub1 then you are likely to have the hard disk formatted with ext3, which hardly has any advantages compared to ext4. 

A fresh install of 14.04.2 LTS (maybe using X/Lubuntu if we are dealing with old hardware) will get rid of 12.04, ext3 and Grub1 in one go.

This is good advice.

> **davehk said:**
> 
but I'd still like to understand why GRUB 1 is not working as it should

.....

Yes, I'm planning to move to 14.04 on a new HDD later this year but don't have time at the moment to get it all set up and then move all my data, emails, website  etc. across.

grub1 is not supported on any Ubuntu distribution at the moment so you may find it difficult to get an answer here as many will not have used it for a long time.

Kind regards

---

### Post by davehk on 2015-05-05
Fair enough - I won't fret about it!

Thanks for all the advice.

---

