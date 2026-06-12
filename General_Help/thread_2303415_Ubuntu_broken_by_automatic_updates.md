---
title: "Ubuntu broken by automatic updates"
date: 2015-11-18
forum: General Help
---

### Post by flix3 on 2015-11-18
Today something terrible happened to my PC.
I cannot log in anymore.
I can see the Ubuntu login screen at a strange screen resolution, but when I insert my correct password, the system tries to init my desktop, fails silently, and then asks me again my password showing me the log screen again and again.

Ubuntu 15.10 64bit. Last package that the update manager installed was something related to Nvidia. And this is strange, since usually the user should decide whether to update the proprietary graphic driver or not.

Please help. I cannot afford a complete reinstall.

---

### Post by flix3 on 2015-11-18
Extremely little improvement.
I've atp-get remove nvidia* from the grub recovery command line.

Now I can login, but the monitor resolution is LOCKED at 640x480.
Also, the Noveau driver is LOCKED.

That means that I'm completely stuck and the system is unusable.

Any help please?

---

### Post by flix3 on 2015-11-18
Solved.

I had to purge Nvidia driver, reboot again and then the Noveau driver was no more locked and I could reinstall the Nvidia driver.

---

### Post by grahammechanical on 2015-11-18
> And this is strange, since usually the user should decide whether to update the proprietary graphic driver or not.

If, in Software & Updates, we have ticked the box "Proprietary drivers for devices (restricted)" the we are are going to get updates for the proprietary video drivers along with any other kind of update available. As I did this morning. It was Nvidia cuda. But I had to run the Update Manager. It was not completely automatic.

It did not break my system. I cannot think why it broke your system. 

Regards.

---

### Post by Lennart_Odeberg on 2015-11-21
I'm having the same problem. How exactly did you purge the Nvidia driver?

---

