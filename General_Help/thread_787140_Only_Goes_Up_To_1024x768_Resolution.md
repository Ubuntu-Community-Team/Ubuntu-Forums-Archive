---
title: "Only Goes Up To 1024x768 Resolution"
date: 2008-05-08
forum: General Help
---

### Post by GameBox 47 on 2008-05-08
Sorry I'm a total Linux n00b.  But I think I forgot to install it in the initial setup for Xserver, any way to get the resolution one step above 1024x768?  (Forgot what it was called)

---

### Post by GameBox 47 on 2008-05-08
Anyone?

---

### Post by GameBox 47 on 2008-05-08
Thanks for all the help guys... no really, what can I do?

---

### Post by FuturePilot on 2008-05-08
We need more information to be able to help you. What graphics card do you have and are you using a restricted driver with it? And what did you forget to install?

---

### Post by GameBox 47 on 2008-05-09
I didn't install any extra drivers.  I think I just configured Xorg wrong during setup, I forgot to put one of the resolutions. :(

However, it's using the i810 Intel driver for the graphics card (Intel 845).

---

### Post by storm99999 on 2008-05-09
Have you tried "sudo dpkg-reconfigure xserver-xorg" in the terminal?  It will place you in a menu to change the settings.

---

### Post by GameBox 47 on 2008-05-09
Thanks, it worked. :)

---

