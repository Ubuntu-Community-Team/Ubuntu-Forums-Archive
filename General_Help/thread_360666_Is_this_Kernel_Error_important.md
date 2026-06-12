---
title: "Is this Kernel Error important?"
date: 2007-02-13
forum: General Help
---

### Post by disturbedite on 2007-02-13
i get this when i update kernels via adept:

W: mdadm: unchecked configuration file: /etc/mdadm/mdadm.conf
W: mdadm: please read /usr/share/doc/mdadm/README.upgrading-2.5.3.gz .
W: mdadm: no arrays defined in configuration file.
W: mdadm: falling back to emergency procedure in initramfs.


i read that this just means that it can't find any raid arrays?  how can i get rid of this even if its not important?  just cuz its kinda cosmetically annoying.

i've attached the output of 
sudo sh -x /usr/sbin/update-grub > $HOME/update-grub.txt 2>&1

---

