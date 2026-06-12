---
title: "Mount Disk on startup"
date: 2008-05-17
forum: General Help
---

### Post by SomeStupidHippie on 2008-05-17
Hello everyone,

First of all, I know that some other threads have been posted about this, but I feel like a really need step by step help, or at least a very detailed pre-made walkthrough, if someone could point me in the right direction. I have used Ubuntu for a while, but I'm still pretty much a noob to a lot of things.

Anyway, I would really like to mount one of my hard drives on startup, without having to enter a password. Just have it appear ready to use on the desktop when I turn my computer on. Its formatted as ext3, and I am more than happy to provide any other information you need. Thanks in advance!

---

### Post by mikewhatever on 2008-05-17
Here is a good guide. [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by SomeStupidHippie on 2008-05-17
Does that guide make it so that it will automatically mount on startup? To me it just looked like a guide for regular mounting, but I could be wrong.

---

### Post by conscious on 2008-05-17
You may find pysdm helpful. To install it, type ```
sudo apt-get install pysdm
``` at the terminal.

---

### Post by Xiong Chiamiov on 2008-05-17
> **SomeStupidHippie said:**
> Does that guide make it so that it will automatically mount on startup? To me it just looked like a guide for regular mounting, but I could be wrong.
That guide will add an entry for your fstab, which manages what gets mounted at startup.

If you need specific help, post the output of
```

sudo fdisk -l

```
and tell us which partition it is you want mounted and where, and we'll be glad to help you.

---

### Post by SomeStupidHippie on 2008-05-20
Thanks concious, that program was really helpfull, got everything straightened out. Thanks to everyone else too, for your suggestions.

---

### Post by btermeli on 2008-05-20
How did u  do that with the program???

---

### Post by pnavarrc on 2009-02-08
The program make this for you. In the left panel, you have partitions. You click in each partiton in order to configure them, and you can mount (and examine) the partitions and change the name of the partition. There are other options also, like permissions.

Unmount and mount again and the changes will have efect, very nice program. Good luck,

   Pablo.

---

