---
title: "Kernel downgrade (16.04) and disk encryption"
date: 2018-04-24
forum: General Help
---

### Post by simon-vrouwenvelder on 2018-04-24
Good afternoon! 


In order to compile a kernel module I need for some experiments (IGH EtherCat), I need to downgrade the kernel version of my Ubuntu (Gnome) 16.04 installation. 

Current Kernel = Linux 4.13.0-39-generic x86_64
HDD is encrypted (used the LVM option for filesystem encryption in the Ubuntu installation procedure)
DE = GNOME

Installed the 4.10 and 4.4 LTS kernel, but when I try to boot them I cannot get passed the screen where I have to provide the password to decrypt my file system. My keyboard seems to be unresponsive ( the screen resolution is affected as well, and it only supports 1 screen). 

Are there any other steps I need to take in order to downgrade the kernel version while having an encrypted filesystem (EXT4)?

---

