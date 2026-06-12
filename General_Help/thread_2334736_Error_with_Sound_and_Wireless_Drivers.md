---
title: "Error with Sound and Wireless Drivers"
date: 2016-08-22
forum: General Help
---

### Post by d.khatri on 2016-08-22
My Ubuntu's sound and WiFi stopped working suddenly. When I upgrade it shows  following error:
Errors were encountered while processing:
 udev
 grub-common
 grub2-common
 grub-pc-bin
 grub-pc
 lightdm
 keyboard-configuration
 console-setup-linux
 console-setup
 network-manager
 upower
 xserver-xorg-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by banceu_sergiu_ione on 2016-08-22
Hi

Can you use a wired connection and run 
```
 sudo apt update 
```
```
 sudo apt upgrade 
```
post the output of apt upgrade with errors, try get the whole output.

---

