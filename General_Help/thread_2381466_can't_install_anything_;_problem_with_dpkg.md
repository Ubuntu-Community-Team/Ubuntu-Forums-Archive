---
title: "can't install anything ; problem with dpkg"
date: 2018-01-01
forum: General Help
---

### Post by viktor03 on 2018-01-01
Hi all,

happy new year !

I can't install any programs anymore... either via CLI or software center i get the message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

when i do that, i get:

viktor@ubuntubox:~$ sudo dpkg --configure -a
Setting up linux-headers-4.13.0-19-generic (4.13.0-19.22) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.13.0-19-generic /boot/vmlinuz-4.13.0-19-generic

and it's just stuck there...

thanks for any help!

Viktor

---

### Post by mörgæs on 2018-01-01
Please run ```
sudo apt update
``` and post the results in CODE tags.

---

### Post by viktor03 on 2018-01-01
i ran "fix broken packages" from a live usb in recovery mode (i was trying to fix my grub after running a proposed fix for a different problem)
anyway, it's working again.

thank you for replying

---

