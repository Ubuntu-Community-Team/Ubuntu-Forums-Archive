---
title: "how to increase Swap file size"
date: 2017-09-30
forum: General Help
---

### Post by cee2 on 2017-09-30
so i installed gparted, can open it but trying to slide the slider when clicked on the main sda1  does not work
nor can i change any variables in the boxes below
whats up?

---

### Post by cee2 on 2017-09-30
i cant unmount the existing partition im using i guess since im logged on and using it so how can i make sda1 smaller so i can make swap file bigger from 8 gb to say 12 or 15 gb?

---

### Post by cee2 on 2017-09-30
nevermind, i figured it out
just used my usb live cd install stick and resized it.

Wooh HOOO it worked obviously since im here typing 3 minutes later
now to see if this soves my freezing problems

---

### Post by oldfred on 2017-09-30
I do not think swap is your issue.
System only uses swap when out of RAM, and if you ahve 4GB or more of RAM you may only run out of RAM if editing videos or a very few other apps.

 Some Gigabyte boards need acpi=off boot parameter also
Gigabyte GA-990FXA-UD3 and 64bit Xubuntu 16.04 LTS install
[https://ubuntuforums.org/showthread.php?t=2370503](https://ubuntuforums.org/showthread.php?t=2370503)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

