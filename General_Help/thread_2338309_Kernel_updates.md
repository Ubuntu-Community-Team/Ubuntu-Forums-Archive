---
title: "Kernel updates"
date: 2016-09-26
forum: General Help
---

### Post by Evil Wayz on 2016-09-26
I switched from the standard 4.4 kernel to the newer 4.7 kernel to resolve some issues with my system.  However, Ubuntu is still constantly updating the 4.4 kernel, which means I have to restart, and then autoremove the old kernels and restart again.  It's annoying.  Should I remove the older kernels completely?  I haven't checked grub but I'm not sure if I have multiple instances of 4.7 for backup in case of a problem.

EDIT:  Here's what's in grub:  
```
 Found linux image: /boot/vmlinuz-4.7.2-040702-generic
Found initrd image: /boot/initrd.img-4.7.2-040702-generic
Found linux image: /boot/vmlinuz-4.7.0-040700rc3-generic
Found initrd image: /boot/initrd.img-4.7.0-040700rc3-generic
Found linux image: /boot/vmlinuz-4.4.0-39-generic
Found initrd image: /boot/initrd.img-4.4.0-39-generic
Found linux image: /boot/vmlinuz-4.3.0-040300-generic
Found initrd image: /boot/initrd.img-4.3.0-040300-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

Running Ubuntu 16.04.1 LTS, with xubuntu desktop, and kernel 4.7.2-040702-generic.

---

### Post by ian-weisser on 2016-09-26
The 'linux-image-generic' (in 16.04) and 'linux-image-virtual-lts-xenial' metapackages will continue to pull the latest 4.4 kernels from the Ubuntu repositories.
Did you remove those metapackages?

---

### Post by Evil Wayz on 2016-09-27
I did not.  According to my system the second metapackage isn't installed. Unless that's not its exact name.

---

### Post by ian-weisser on 2016-09-27
Go ahead and remove the one you have. That should stop pulling in kernels from the Ubuntu repositories.
You can always add it again if you change your mind.
```
sudo apt remove linux-image-generic
```

---

### Post by Evil Wayz on 2016-09-27
Thanks, I'll try that.

---

