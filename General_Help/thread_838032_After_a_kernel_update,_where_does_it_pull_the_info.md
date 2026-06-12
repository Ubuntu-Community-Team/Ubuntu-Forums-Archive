---
title: "After a kernel update, where does it pull the info from to rebuild menu.lst?"
date: 2008-06-23
forum: General Help
---

### Post by Rich99 on 2008-06-23
I moved a 6.06LTS install across from a machine with ATA disks to one with SATA disks.  This required updating the lines in /boot/grub/menu.lst from boot=/dev/hda1 to boot/dev/sda1.  However whenever I update the kernel and it adds a line for the new kernel, it reverts to hda1, so I have to remember to correct menu.lst before I reboot (the machine's headless so boot problems are a pain).  Where does it pull the info from, so I can change it so that it always uses sda instead of hda when adding lines for new kernels?

---

### Post by plucky on 2008-06-23
> Where does it pull the info from, so I can change it so that it always uses sda instead of hda when adding lines for new kernels?


The information is stored in the menu.lst file.

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
gksudo gedit /boot/grub/menu.lst
```

and scroll down till you reach

> ## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# [color=red]kopt=root=UUID=03aa7483-5b8f-4c1e-bd09-5db055ead5eb ro[/color]


The latest menu.lst uses UUID's instead of /dev/sda,but if you change the the highlighted entry,it will change the boot entry when there are kernel updates.(Do not remove the # in front of the line).

There are other options that you can set in menu.lst so that kernel updates keep the same options,just scroll through your menu.lst file and read the options. Adjust to suit your requirements.

Good Luck

---

### Post by louieb on 2008-06-23
Nice explanation of the various automagic options here.
 [GrubHowto - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GrubHowto#head-1296ce2b184032373f19ad50a91d506eb886ac5f")

---

### Post by Rich99 on 2008-06-23
LOL - can't believe I never noticed those options!  I just skipped over all the comments before now!  Thanks for pointing them out :)

---

### Post by drs305 on 2008-06-23
You can use Startup-Manager to safely make changes to the grub menu display without manually editing menu.lst. Here is more information about how to tweak menu.lst:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

