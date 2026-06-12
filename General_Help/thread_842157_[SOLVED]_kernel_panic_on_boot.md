---
title: "[SOLVED] kernel panic on boot"
date: 2008-06-27
forum: General Help
---

### Post by Big_Croc7 on 2008-06-27
This is more of an informational point than a request for help.  I removed some old kernels and modules to free up space, and afterwards when I boot I get the following sequence:

Ok, booting the kernel
RAMDISK: ran out of compressed information
error: invalid compressed format (err=1)
kernel panic

It's not a problem, as I left a few older kernels, so I can still boot - the problem only happens with the most recent I have (.52).  .51 works fine.  I also don't have much time to test it at the moment to find out what's happened, but in case someone wants to look into it, all I did was remove the kernel image and restricted module packages using synaptic, I think it was for versions .27 and .28.

---

### Post by Rocket2DMn on 2008-06-27
Try updating GRUB
```
sudo update-grub
```
This should remove old kernels from the grub list.  If you search in Synaptic you can look for "linux-image" and mark the kernels you want for Complete Removal - this is the best way to approach removing old kernels I believe.  You can also state in your /boot/grub/menu.lst file how many kernels to show.  Look for the line
```
# howmany=all
```
and change to something like
```
# howmany=3
```
Save and close, then run the update-grub command.

---

### Post by Big_Croc7 on 2008-06-30
Thanks - I don't think it's a problem with grub though as I still have the 2.6.15.52 image package installed.  I removed 27 & 28 I think, and these got deleted from the grub menu automatically.  I didn't do a purge though, so maybe you're right and it is old config files causing a problem.

---

### Post by chrisccoulson on 2008-06-30
Sounds like a corrupt initamfs. Did you run out of disk space on /boot during a kernel upgrade? That can cause the building of the initramfs to fail. Try booting to your older kernel and run the following:
```
sudo update-initramfs -u
```

This will recreate the initramfs for the newest kernel on the system. If the one which is broken isn't the latest version, use the '-k' option to specify a kernel version (ie, 2.6.15-52-386 for Dapper i386 kernel)

---

### Post by Big_Croc7 on 2008-07-03
I purged and installed the .52 kernel package (and also the pseudo-packages), and that seems to have fixed it.  I guess it was probably as you say, a problem with an update, and just by coincedence I removed the .27 and .28 packages at the same time as an automatic upgrade so I thought it was related.

:D

---

