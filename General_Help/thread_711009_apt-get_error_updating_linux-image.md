---
title: "apt-get error updating linux-image"
date: 2008-02-29
forum: General Help
---

### Post by ricperry1 on 2008-02-29
I have searched for a solution to my problem, but as yet have not encountered this error on any of the forums.  It's probably buried somewhere, but if someone would please review my situation, hopefully my error/mistake/problem is obvious...  I can post more details if it helps, but here is my output from an "apt-get upgrade":

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-2.6.22-14-generic (2.6.22-14.52) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.22-14.46 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 3
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ricperry1 on 2008-02-29
Turns out the error was in my /boot/grub/menu.lst file.  I had the entry "default saved" without a "savedefault" boot entry.

---

### Post by ensimismada on 2008-05-24
I'm having the exact same problem with the same package. As advised, I checked my /boot/grub/menu.lst. I had default saved, but savedefault was commented out and set to false. So I uncommented that line, changed it to true, saved, and ran apt-get -f install again. No luck; it gave me the exact same error message as before, identical to that of the first post in this thread. 

Could you please describe your fix in more detail? Thanks. :)

---

