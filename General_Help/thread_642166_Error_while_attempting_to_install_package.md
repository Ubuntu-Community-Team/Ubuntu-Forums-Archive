---
title: "Error while attempting to install package"
date: 2007-12-16
forum: General Help
---

### Post by timbounceback on 2007-12-16
tim@tim-laptop:~$ sudo apt-get install <package>
[sudo] password for tim:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
tim@tim-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.23.1
Cannot find /lib/modules/2.6.23.1
update-initramfs: failed for /boot/initrd.img-2.6.23.1
dpkg: subprocess post-installation script returned error exit status 1
tim@tim-laptop:~$ 

Some googling reveals that this happens when you make a mistake compiling your own kernel, yet I haven't done that (at least not recently). Any suggestions?

---

### Post by Pumalite on 2007-12-16
Where did you get kernel xxx-23.1?

---

### Post by timbounceback on 2007-12-16
I recently installed Zenwalk (having later formatted it), and the kernel it came with was 23.1 - could that have something to do with it?

---

### Post by Pumalite on 2007-12-16
As far as I know, we are running kernel xxxx-14-generic
Post output of:
uname -a

---

### Post by timbounceback on 2007-12-16
that's correct:
Linux tim-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

---

### Post by Pumalite on 2007-12-16
Remove the other kernel. Or better yet start from scratch and this time use Gparted Live CD to delete and make a new partition. Your system seems unstable.

---

### Post by timbounceback on 2007-12-16
How would I go about removing the other kernel - should I just remove the img file in /boot?

---

### Post by Pumalite on 2007-12-16
How did it get in /boot in the first place?

---

### Post by timbounceback on 2007-12-16
I have no clue.... I also recently installed Sabayon, which made it's own /boot partition (which I again, later formatted, both the boot partition and the main partition), so perhaps this might have something to do with it to?

---

### Post by Pumalite on 2007-12-16
I think you better save data and start from scratch.

---

### Post by timbounceback on 2007-12-16
Ah well.... I suppose I'll have to - I'll do that tonight. Thanks for your help :-).

---

### Post by Pumalite on 2007-12-16
You are welcome. Keep it clean.

---

