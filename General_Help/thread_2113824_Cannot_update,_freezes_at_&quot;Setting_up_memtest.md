---
title: "Cannot update, freezes at &quot;Setting up memtest86+&quot;"
date: 2013-02-08
forum: General Help
---

### Post by Selvinus on 2013-02-08
Hi folks!

Got some problems with my Ubuntu 12.10. When I try to run update manager everything freezes at "Setting up memtest86+".  

```
sudo apt-get update
``` after a fresh restart returns this message:

```
dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```Running ```
sudo dpkg --configure -a
``` returns this:
```

Setting up memtest86+ (4.20-1.1ubuntu2.1) ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-18-generic
Found initrd image: /boot/initrd.img-3.5.0-18-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
grub-probe: error: cannot find a GRUB drive for /dev/sdc1.  Check your device.map.
grub-probe: error: cannot find a GRUB drive for /dev/sdd1.  Check your device.map.
Found Windows 8 (loader) on /dev/sda1
Skipping Windows 8 (loader) on Wubi system
done


```and then everything just freezes again, nothing happens.

Anyone have some tips? Broken packages?

---

### Post by guy2545 on 2013-02-08
I'm having the same problem.  I have not found a solution yet, just replying so I can remember to come back to this thread.

---

### Post by Selvinus on 2013-02-09
Anyone? I would love to avoid installing Ubuntu all over again.. :(

---

### Post by Selvinus on 2013-02-12
I switched over to Ubuntu 12.04 LTS, everything is working fine now. Looks like it is a 12.10 specific problem.

---

