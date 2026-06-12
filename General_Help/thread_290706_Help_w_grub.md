---
title: "Help w/ grub"
date: 2006-11-01
forum: General Help
---

### Post by igknighted on 2006-11-01
I installed ubuntu onto one of my hard disks, and there was a gentoo (Sabayon) install on another disc.  I let ubuntu write its own grub figuring it would probably see the other install, but no such luck.  I have gotten the system to load the kernel and (i believe) specified the proper initrd, but the boot halts when I get to
```
The root block device is unspecified or not detected.
Please specify a device to boot, or "shell" for a shell...
boot() ::
```
What should i put here, or even better what should the entry look like menu.lst?

edit: Currently the menu.lst entry looks like this
```
title     Sabayon Linux 3.1
root       (hd2,0)
kernel     /vmlinuz root=/dev/sda1 ro
initrd     /initramfs-genkernel-x86_64-2.6.18-gentoo
boot 
```

---

### Post by matthewstory on 2006-11-01
the root block device is specified higher up in the menu.lst file, and comes after a # delimeter, which needs to be there, the section should you're looking for should look like this:

## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

In addition you may also have to reconfig your device.map

shell~$ sudo grub --device-map=/boot/grub/device.map

    >> root (hd0,0)
    >> setup (hd0)
    >> quit

hope this helps.

---

