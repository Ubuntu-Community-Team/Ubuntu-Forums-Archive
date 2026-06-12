---
title: "Customizing Grub so windoze is first in the list?"
date: 2007-06-02
forum: General Help
---

### Post by xl_cheese on 2007-06-02
Currently Ubuntu is the first on tlhe list and will boot once the timer runs down.  Can I change it so windows is the first on the list to boot?

thanks.

---

### Post by mikewhatever on 2007-06-02
Here is the guide [http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by tagra123 on 2007-06-02
Open the text editor

```
gksudo gedit /boot/grub/menu.lst
```


Find the line

### BEGIN AUTOMAGIC KERNELS LIST

If you place the windows boot section above this line it will always remain first in the list even after updates.

When finished it should look something like this

```

 title		Windows 95/98/NT/2000
 root		(hd0,0)
 makeactive
 chainloader	+1

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
# kopt=root=/dev/hdc1 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-26-k7
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
title    SystemRescueCd 
kernel   (hd1,1)/sysrcd/vmlinuz1 root=/dev/ram0 vga=788 bootfrom=/dev/hdb2 init=/linuxrc setkmap=us
initrd   (hd1,1)/sysrcd/initrd1
boot


```

---

