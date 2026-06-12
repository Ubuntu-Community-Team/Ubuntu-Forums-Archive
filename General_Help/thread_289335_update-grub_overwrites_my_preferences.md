---
title: "update-grub overwrites my preferences"
date: 2006-10-30
forum: General Help
---

### Post by JackDog on 2006-10-30
Is /boot/grub/menu.lst the best place to override grub defaults? All I want to do is specify "defoptions=quiet splash vga=791" but everytime I run update-grub or synaptic updates, my changes are lost.

---

### Post by yabbadabbadont on 2006-10-30
You should be able to change them directly in the default menu.lst file:
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
# kopt=root=/dev/hda3 ro

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
# defoptions=vga=791 quiet

```
You will notice that I have added "vga-791" to my defopitons.  After you do that, run update-grub and it will apply the change to all the kernel lines.

If that is what you have done and you still have problems, please post your menu.lst file.

---

### Post by JackDog on 2006-10-30
Thanks, I was removing the # sign. Apparently update-grub wants one # before the line. I had none.

---

### Post by yabbadabbadont on 2006-10-30
I thought that might be the problem.  That's why I posted a working example. :D   I'm glad it helped.

---

