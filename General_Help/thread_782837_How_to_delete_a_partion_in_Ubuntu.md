---
title: "How to delete a partion in Ubuntu"
date: 2008-05-05
forum: General Help
---

### Post by jakeruston on 2008-05-05
Hi,

I had a Windows Vista Partion, and a Ubuntu Partion. I wanted Ubuntu on its own, so I reinstalled Ubuntu again, trying to remove them both and start again. However, I only deleted the Windows Vista partion and got another Ubuntu, which has left me with two partions, both with Ubuntu on.

How can I delete the one I just installed in Ubuntu?

Thanks,
Jake Ruston.

---

### Post by TeoBigusGeekus on 2008-05-05
Type in a terminal
```
sudo apt-get install gparted
```

Then again 
```
gparted
```

to open gnome-partition editor. You can do whatever alterations to your partitions from there.

---

### Post by jakeruston on 2008-05-05
Okay thanks. I think I'm on the first Partion at the moment, so do I need to open hdb1, and try to delete or resize everything in there?

---

### Post by TeoBigusGeekus on 2008-05-05
If your first installation is on hda1, you need to format hdb1, in which lies your second installation.
You can keep it if you want as a separate partition. But if you want to resize hda1, so that it absorbs hdb1, you need to do this from the live cd, because gparted cannot operate on a mounted partition and if you are running Ubuntu, that means that hda1 is mounted.
If you use the live cd, just type
```
gparted
```
in terminal.

---

