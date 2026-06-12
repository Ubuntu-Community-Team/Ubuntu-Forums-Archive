---
title: "Dumb Move..."
date: 2008-04-28
forum: General Help
---

### Post by chet richaldson on 2008-04-28
So yesterday I figured Ide clean up Windows XP and did a disk cleanup and checked off a few of the boxes of files to delete/compress...

Now I try to get back into Ubuntu this morning and im getting an Error 17 - File missing or something like that...which im guessing is due to what I did in XP.

I guess my question here is firstly, can I undo what I did in windows? I tried system restore but that had no effect.  Secondly, can I re-install wubi without losing all my settings, updates and installations on Ubuntu?  Any help would be greatly appreciated guys.  Thanks.

---

### Post by ago on 2008-04-28
If you still have c:\ubuntu\disks (and particularly root.disk) in place you should be in a good shape. Just make sure those are not overwritten or deleted.

---

### Post by chet richaldson on 2008-04-28
I dont have an Ubuntu folder in my C:... I do have a wubi file which has a 'disks' folder.  It has 3 files in it... home.virtual.disk,  swap.virtual.disk   and   system.virtual.disk.

---

### Post by ago on 2008-04-28
That is a 7.04 installation probably
8.04 will use C:\ubuntu\disks

---

### Post by chet richaldson on 2008-04-28
So what should I do with the files?  Save them, uninstall wubi, reinstall wubi and put those files back from where i took them or what?

---

### Post by ago on 2008-04-28
There are recovery tools to restore them, but I do not have much experience with those.

---

