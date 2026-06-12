---
title: "mouse sort of working but not really? 12.10"
date: 2012-10-21
forum: General Help
---

### Post by valke on 2012-10-21
fresh install of 12.10. i've not made any changes at all. i have a generic wired usb logitech mouse (a B100 model) that the cursor moves but none of the buttons work. i also have a r.a.t. 5 that it's almost the same as the logitech but i can (sometimes) click on the unity buttons in the launcher. 

could i please get a bit of assistance?

thanks

---

### Post by ~LoKe on 2012-10-21
> **valke said:**
> fresh install of 12.10. i've not made any changes at all. i have a generic wired usb logitech mouse (a B100 model) that the cursor moves but none of the buttons work. i also have a r.a.t. 5 that it's almost the same as the logitech but i can (sometimes) click on the unity buttons in the launcher. 

could i please get a bit of assistance?

thanks

Had this problem too.  Try logging out and logging back in.

---

### Post by valke on 2012-10-21
sadly, i did. i rebooted a few times as well.

---

### Post by ~LoKe on 2012-10-21
Odd.  For me, rebooting doesn't fix it.  I have to log out (ctrl+alt+del) and log back in, then everything's fine.

---

### Post by PHYD0UX on 2012-12-14
It comes and goes. I find if I have more than one program running it tends to do that. Is there a fix for this yet?

---

### Post by seanmp on 2013-03-02
i was cumming across the same problem with my computer so after a while i found that if you type this into the terminal it can fix the problem:


sudo apt-get install --reinstall xserver-xorg-input-mouse xserver-xorg-input-evdev-dev

---

### Post by jrewolinski on 2013-04-07
> **seanmp said:**
> i was cumming across the same problem with my computer so after a while i found that if you type this into the terminal it can fix the problem:


sudo apt-get install --reinstall xserver-xorg-input-mouse xserver-xorg-input-evdev-dev

This works for me, but after a reboot it's broken again.  I can click on anything in the Unity (believe that's what it's called now) menu, but not inside of any other windows.  Basically the Finger Pointer is broken.

I have a Razer Mamba 2012 if it makes any difference.

---

