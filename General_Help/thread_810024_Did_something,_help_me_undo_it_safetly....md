---
title: "Did something, help me undo it safetly..."
date: 2008-05-27
forum: General Help
---

### Post by jbaerbock on 2008-05-27
Ok so I was following instructions on how to mount a certain mp3 player. Long story short it did not work but one thing I did was:

sudo mount /dev/sda1 /dev/mp3

I had created the mp3 folder before hand.

Well now when i click on the mp3 folder it comes up with the same contents as what my ntfs windows partition has in it (my guess is normaly this was on sda1 hence the problem). So how would I undo whatever happened? Wouldn't have been files moved since it took but a second for operation to complete. Would something like the following work:

sudo mount /dev/mp3 /dev/sda1

---

### Post by pointone on 2008-05-27
Firstly--do not ever create/remove things in "/dev". "/dev" is populated by the computing gods.

To undo a mount, umount:

```
sudo umount /dev/mp3
sudo rmdir /dev/mp3
```

Mounting does not move any files/data around--it simply makes the drive accessible. If you made any changes to the files you saw, however, that's another story.

Mount things in "/mnt"; that's what it's for.

---

### Post by jbaerbock on 2008-05-28
Good advice lol. I'll try it when i get home. It didn't mess anything up and I was smart enough not to modify the files in said folder. Thanks again.

---

### Post by jbaerbock on 2008-05-28
Well it seems Linux is smarter than I for when I booted this morning to make those changed the mp3 folder was already gone and everything back to normal lol, go figure!

---

### Post by chrisccoulson on 2008-05-28
/dev is a volatile filesystem (tmpfs) and is populated by UDEV, so any changes you make to it are temporary. However, playing around in /dev could very well lead to a system crash, or at worst, hosing a disk (which won't be temporary!)

---

### Post by jbaerbock on 2008-05-29
Yeah good to know, I'll steer clear from now on. I knew the command wouldn't damage anything just didn't know how to undo to it (hence why I asked) in a known safe manner.

---

