---
title: "startupmanager bricks my box"
date: 2007-12-29
forum: General Help
---

### Post by schmolch on 2007-12-29
I installed the startupmanager because i wanted my default ubuntu splash back.
So i ran it and chose the ubuntu splash but afterwards the box wont boot anymore.
The boot-process stops immediately after grub, no errors appear on the console, it just doesnt do anything.
I tried it several times and obviously the initrd file that startupmanager writes is not working. Fortunately there is still the initrd backup file which i can boot.

I did nothing else but select the default ubuntu splash in startupmanager, i did no other changes.

I think i will file a critical bug about this.

---

### Post by tgilber1 on 2007-12-29
> **schmolch said:**
> I installed the startupmanager because i wanted my default ubuntu splash back.
So i ran it and chose the ubuntu splash but afterwards the box wont boot anymore.
The boot-process stops immediately after grub, no errors appear on the console, it just doesnt do anything.
I tried it several times and obviously the initrd file that startupmanager writes is not working. Fortunately there is still the initrd backup file which i can boot.

I did nothing else but select the default ubuntu splash in startupmanager, i did no other changes.

I think i will file a critical bug about this.

Try the installation CD and choose the rescue option.  Possible solution may be to get to the GRUB command line

root (hdx, x) x=[0-9]
setup (hdx)
reboot

ex.
root  (hd0,0)
setup (hd0)
reboot

---

### Post by schmolch on 2007-12-29
I know how to repair it, the point is that startupmanager is not supposed to do the damage.

---

### Post by wpshooter on 2008-05-30
> **schmolch said:**
> I know how to repair it, the point is that startupmanager is not supposed to do the damage.

I agree with you, this StartupManager program seems to cause all kind of problems when you use it.  I sort of thought the purpose of this was to be able to customize certain things but instead what it winds up doing is breaking things.

Good luck on getting this fixed.

---

