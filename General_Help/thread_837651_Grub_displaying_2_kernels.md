---
title: "Grub displaying 2 kernels?"
date: 2008-06-22
forum: General Help
---

### Post by joe56 on 2008-06-22
First of all I love ndiswrapper. Following verbatim [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419) (minus the last step: adding lines to /etc/network/interfaces) I was able to get my D-Link DWL-G122 rev. B1 working in Hardy. Judging by the amount of similar posts about the rt2500 chipset I got lucky which is good considering my limited experience with Linux. So thanks to the community for the solution to that problem.

Now...Since I have a working connection in Ubuntu for the first time in a couple months, I just did over 200Mb of updates. Upon rebooting, I notice in grub I have 4 Ubuntu boot options. 


kernel *version*-19    
kernel *version*-19(recovery)
kernel *version*-16    
kernel *version*-16(recovery)

How can i get rid of the older 16's, or is there any benefit to keeping both? Thanks!!

---

### Post by exploder on 2008-06-22
To get rid of the old kernel, open Synaptic and remove the -16 ubuntu-restricted-modules first. It is extremely important to remove this first! Next remove the other -16 kernel packages.

Now you should just have the current kernel.

---

### Post by Vivaldi Gloria on 2008-06-22
You can comment out the relevant lines for kernel-some-version in your

```
/boot/grub/menu.lst
```

to get rid of the kernels you dont want. For example the lines of my menu.lst for kernel 2.6.24-16-generic looks like this:

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```

To get rid of kernel 2.6.24-16-generic I need to change it to

```
#title		Ubuntu 8.04, kernel 2.6.24-16-generic
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fb18d006-4ec8-41d3-bb25-8a1f643a99aa ro quiet splash
#initrd		/boot/initrd.img-2.6.24-16-generic
#quiet
```

So to comment out a line you put # at the beginning. Now this kernel won't appear in the grub menu. This method doesn't delete the kernel from your hd so you can enable it in the future by deleting the # signs you added.

If you want you can also completely remove kernels using synaptic.

I suggest you keep at least two different versions of the kernel in case the first one gets broken. I just keep all as I have enough hd space.

---

### Post by joe56 on 2008-06-22
Thanks to both of you, my question has been answered.

---

### Post by drs305 on 2008-06-22
Startup-Manager is a safe alternative to manually editing grub's menu.lst
The menu.lst will automatically be updated when older kernels are removed via synaptic. 

To learn more about Startup-Manager and grub boot displays:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

