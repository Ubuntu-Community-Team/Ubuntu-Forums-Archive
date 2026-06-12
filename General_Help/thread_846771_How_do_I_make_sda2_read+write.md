---
title: "How do I make sda2 read+write"
date: 2008-07-01
forum: General Help
---

### Post by Amalaye on 2008-07-01
sda2 is an NTFS partition where some variant of Windows lives (XP server). However I now need to move my /home dir to it and do a clean install.

How do I make this partition writable? It is auto mounted somehow and I would like to use it to stash some stuff I want to preserve.

I am running Ubuntu ... Edgy ...

---

### Post by lswb on 2008-07-01
Just to be clear on your intentions, do you mean to permanently remove windows from sda2 and convert it to a linux partition? What do you want to install with the "clean install" I'm hesitant to give any advice without knowing for sure what you want to accomplish.

---

### Post by soccerboy on 2008-07-01
wants to move the /home partition into sda2.  wants to clean install linux.  can we get your output from ```
mount
```

---

### Post by Amalaye on 2008-07-02
I figured I need to use mount. Ubuntu automagically mounts sda2 as a read only file system (I have no idea how it does this). So now I would like Ubuntu to mount it as a read/write file system.

Do I unmount then mount again?

---

