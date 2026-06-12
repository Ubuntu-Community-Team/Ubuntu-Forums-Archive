---
title: "Cannot save Abi file to floppy"
date: 2008-06-23
forum: General Help
---

### Post by paddy1 on 2008-06-23
I am trying to save an Abi file as a microsoft DOC file to my floppy disk. How can I access my floppy drive, if it does not show up in "Places" on the "save file as" window? The floppy drive shows on the desktop, but the desktop in "Places" on the "save file as" window does not show the floppy drive. I have tried "browse for other folders" tab and gone to "file system","floppy", but will not work there saying "folder is write protected". Thanks

---

### Post by ajgreeny on 2008-06-23
You need to mount the floppy disk first.  Put a disk in the drive and then probably the best way is to use the disk mounter applet in the panel, add it if you don't have it, it's very useful if like me, you like to keep other disks, eg winXP, unmounted until you need them.  You should then be able to save to it, I think.

If you want to avoid adding the disk mounter applet just use the terminal to mount the disk with ```
mount /media/floppy0
```Depending on your /etc/fstab file you may need to mount it with root authority, but it shouldn't be necessary, though if that command does not work use ```
sudo mount /media/floppy0
```

Just for interest, the floppy line in my fstab file is:-
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
If yours is different, you may like to try that as mine works with what I've just suggested - I've just tried it.

---

### Post by paddy1 on 2008-06-23
When I go to save to floppy, it says "it is write protected", and will not save

---

### Post by ajgreeny on 2008-06-23
Check the disk protect tab is not in the "Lock" position.  The left hand one should be closed, not an open hole like the one on the right.

---

