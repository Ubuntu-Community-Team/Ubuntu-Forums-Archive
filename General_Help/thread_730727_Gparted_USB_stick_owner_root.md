---
title: "Gparted USB stick owner root?"
date: 2008-03-21
forum: General Help
---

### Post by dmitrijledkov on 2008-03-21
Hmm i just formated my usb stick using gparted into ext3. Now it says that the owner is root and I can't write anything to the stick.

I want a totally open for all stick so that anyone can read and write to it (other computers as well). How do I do that?

Or is there any reason why freshly formated ext3 from gparted is owned by root? Gparted didn't ask for my password.

---

### Post by justleen on 2008-03-21
try to change the ownership of the mount point? 
```

sudo chown user:group /media/usbstick

```

---

### Post by dmitrijledkov on 2008-03-21
I did that thankx.

---

