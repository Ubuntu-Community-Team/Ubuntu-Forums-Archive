---
title: "PS/2 keyboard not working after boot (Kubuntu)"
date: 2008-01-16
forum: General Help
---

### Post by dresnu on 2008-01-16
Hello, I have a ps/2 keyboard attached to the desktop but whenever I boot into kubuntu gutsy I can't type the password in the kdm login page. If I unplug the kb and replug it it works perfectly.
I suspect it is an xkb problem but I don't know how to solve it. I've tried reconfiguring the xserver but that didn't help.
Keyboard works if I boot into recovery mode and also in grub.

Any ideas?

---

### Post by geraldm on 2008-01-17
Please check in your BIOS to see if there is some option that turns the keyboard off.
What is in the section for the keyboard in the file /etc/X11/xorg.conf?

Gerald

---

### Post by dresnu on 2008-01-17
Yes, actually the bios was the problem. There was no option for the keyboard but after upgrading to the latest version I have keys working again.

Thanks.

---

