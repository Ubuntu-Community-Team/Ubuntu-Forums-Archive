---
title: "Initramfs creation fails after nightly system updates"
date: 2019-07-16
forum: General Help
---

### Post by paranoidfactoid on 2019-07-16
Running Ubuntu 18.04.2 with 4.18.0-25-lowlatency. When creating an initialramfs I get 

> 
Calling hook plymouth
Adding binary /usr/lib/x86_64-linux-gnu/plymouth//script.so
E: /usr/share/initramfs-tools/hooks/plymouth/ failed with return 1
Removing /boot/initrd.img-4.18.0-25-lowlatency.dpkg-bak
update-initramfs: failed for /boot/initrd.img-4.18.0-25-lowlatency with 1
#


Note the double // "plymouth//script.so" which looks like a configuration error to me. 

Anyone else seeing this? It's hosed my desktop as gdm3 can't start a display server now. 

I did try reinstalling plymouth and all its dependencies with 

# apt-get install --reinstall plymouth-*

which worked, but ran into the same problem again.

---

