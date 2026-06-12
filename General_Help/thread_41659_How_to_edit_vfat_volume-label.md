---
title: "How to edit vfat volume-label?"
date: 2005-06-14
forum: General Help
---

### Post by Akoluth of Nandus on 2005-06-14
Hello,

i want to edit the volume-label of a vfat partition that is on a usb-stick.
On a ext2/3 partition i can achieve this by using "tune2fs -L [volume-name] [device]" but I have no Idea how to do this with a vfat partition.

Which tool is abled to do that?

---

### Post by Gandalf on 2005-06-14
[QUOTE=Akoluth of Nandus]Hello,

i want to edit the volume-label of a vfat partition that is on a usb-stick.
On a ext2/3 partition i can achieve this by using "tune2fs -L [volume-name] [device]" but I have no Idea how to do this with a vfat partition.

Which tool is abled to do that?[/QUOTE]
 hmmm... i guess gparted can do that,
sudo apt-get install gparted

---

### Post by Akoluth of Nandus on 2005-06-14
[QUOTE=Gandalf]hmmm... i guess gparted can do that,
sudo apt-get install gparted[/QUOTE]
I had a look at gparted but it seems not to support that. Or have I failed to notice it?

---

