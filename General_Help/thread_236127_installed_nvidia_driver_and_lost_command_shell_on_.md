---
title: "installed nvidia driver and lost command shell on dell d820"
date: 2006-08-14
forum: General Help
---

### Post by djsamsel on 2006-08-14
i installed the nvidia driver, have the nvidia splash screen. but if i drop out to command shell by killing gdm or by ctrl-alt-f2 i get a black screen. any ideas? thanks for the help.

---

### Post by [h2o] on 2006-08-14
> **djsamsel said:**
> i installed the nvidia driver, have the nvidia splash screen. but if i drop out to command shell by killing gdm or by ctrl-alt-f2 i get a black screen. any ideas? thanks for the help.

Try booting with boot option "vga=792". On grub menu, choose kernel to load and press e. Add above string last in "kernel" string (not at a Linux box right now, so I can't check" and then boot it.

---

### Post by djsamsel on 2006-08-14
> **'[h2o] said:**
> Try booting with boot option "vga=792". On grub menu, choose kernel to load and press e. Add above string last in "kernel" string (not at a Linux box right now, so I can't check" and then boot it.

it has no effect. as soon as gdm loads, if i try to go back to command line the screen is black.

---

### Post by djsamsel on 2006-08-14
bump. i've reinstalled the entire os. reinstalled the nvidia drivers and the same thing has happened. if i hit ctrl-alt-f2 i get a blank screen. when i shutdown, i get a blank screen until the computer reboots, then grub shows up and my splash follows. any ideas?

---

### Post by 5-HT on 2006-08-15
If you stop using Ubuntu's splash screen on boot you'll be able to see your virtual terminals and the boot/shutdown messages using nvidia's drivers. 
To try it out, follow [h2o]'s post but remove 'splash' instead of adding vga=xxx. To make it permanent, you'll have to make the same change in /boot/grub/menu.lst

---

### Post by elvisd on 2006-08-28
hi djsamsel,

have you solved your issue? same problem here...
but i don't like to remove the splash... :-)
kind regards

elvisd

---

### Post by djsamsel on 2006-08-28
actually, the second time i tried vga=792, it worked. good luck. doug

---

