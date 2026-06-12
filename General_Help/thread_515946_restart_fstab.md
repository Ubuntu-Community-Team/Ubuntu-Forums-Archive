---
title: "restart fstab"
date: 2007-08-02
forum: General Help
---

### Post by stchman on 2007-08-02
Hello all, I am wanting to know a way to restart the drive mountings.  When I edit the fstab file I have to reboot for the changes to take effect?

Is there a command to restart the drive mounting process?

Thanks

---

### Post by milosz.galazka on 2007-08-02
you can mount all devices by using

sudo mount -a

and umount them all

sudo umount -a

umount will show errors if there are open files also this command (with -a parameter) is used only in special cases :)

---

### Post by Old *ix Geek on 2007-08-02
Reboot? This isn't windoze. :lolflag:

At a command line, type this:
**mount -a**

That should do it, but for more options/info, type:
**man mount**

---

### Post by stchman on 2007-08-02
> **milosz.galazka said:**
> you can mount all devices by using

sudo mount -a

and umount them all

sudo umount -a

umount will show errors if there are open files also this command (with -a parameter) is used only in special cases :)

So when you envoke

sudo mount -a

It will mount all the drives in your fstab?

If so then thank you.

---

### Post by milosz.galazka on 2007-08-02
Yes, *man mount* will give more informations
Thanks

---

