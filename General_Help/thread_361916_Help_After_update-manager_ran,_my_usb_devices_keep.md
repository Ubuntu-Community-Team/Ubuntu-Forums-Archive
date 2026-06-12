---
title: "Help: After update-manager ran, my usb devices keep stopping"
date: 2007-02-14
forum: General Help
---

### Post by seanwnz on 2007-02-14
Hi everyone, 

I am running Ubuntu 6.10 on a Toshiba Satellite M70.

Everything was fine until I did a recent package update, since then my usb keyboard and mouse keep getting disabled seconds after it boots into the desktop.

Of course this is rather frustrating have to revert back to the laptop keyboard and trackpad.

Help please? I have no idea what to do.
Let me know what info you need.

Thanks
Sean

---

### Post by gradedcheese on 2007-02-15
As a test, reboot and select the next older kernel from the grub menu that briefly shows up.  It may be that the latest kernel upgrade broke support for these devices and you just need to wait for new drivers.  You can continue using the previous kernel if that works.

---

### Post by seanwnz on 2007-02-15
Great idea -

I only run Ubuntu on my machine though, so Grub doesn't appear.

How do I get the menu to come up on boot?

Thanks

---

### Post by gradedcheese on 2007-02-15
watch closely when powering on, right after the BIOS, you will have the opportunity to press ESC for the grub menu.

---

### Post by seanwnz on 2007-02-15
Tried that, still no good.

Any further suggestions?

---

### Post by gradedcheese on 2007-02-15
ok.  try reconfiguring X (with those devices connected).  This is a shot in the dark, but maybe it will help:

sudo dpkg --reconfigure xserver-xorg

Then restart X (log out and back in or if you don't have any unsaved work open, Control+Alt+Backspace)

---

### Post by seanwnz on 2007-02-15
No that doesn't seem to help either... 

The mouse and keyboard (both running on USB) stop working about 10 seconds after booting into the desktop environment... 

I've tried booting with everything unplugged too, then waiting a minute, then plugging everything in - but they still freeze.

Any more suggestions welcome :)

---

