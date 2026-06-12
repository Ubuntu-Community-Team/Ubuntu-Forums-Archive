---
title: "New user - Libvirt Qemu"
date: 2018-04-23
forum: General Help
---

### Post by tjsilver on 2018-04-23
Hello!

I've just installed Oracle VM on Ubuntu 16.04 and have noticed that there is now a new user by the name of Libvirt Qemu.  I've read that this is a configuration error and elsewhere that I can just delete that user.

It's not really a big issue - I just find it annoying!

The 'virt' bit of the name suggests something to do with VM but there was no mention that a new user would be created.  Change the config. or delete the user - which should I do?

Tim

---

### Post by kerry_s on 2018-04-23
do nothing. 
virtual machines works under that user. for the elevated privileges needed & to maintain security.
i use virtual machine manager & it's setup the same way.

---

### Post by tjsilver on 2018-04-23
Thank you! (I'll just have to learn not to let it bother me)

---

### Post by Dennis N on 2018-04-23
> **tjsilver said:**
> Thank you! (I'll just have to learn not to let it bother me)

I've had libvirt-qemu show up as one of the users on the log in screen (listed below the log in box). If that is where you noticed it, you might be able to suppress it. Could happen in slick-greeter (where I had it showing) and maybe lightdm-gtk-greeter. It bothered me too.

---

