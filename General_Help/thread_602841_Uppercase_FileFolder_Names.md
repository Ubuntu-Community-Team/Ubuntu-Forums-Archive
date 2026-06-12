---
title: "Uppercase File/Folder Names"
date: 2007-11-04
forum: General Help
---

### Post by grineyfase on 2007-11-04
On my internal FAT partition, and on my external hard drive, file or folder names that are all capital are changed to lowercase.

Example:

ATB => atb
CKY => cky
A => a
B => b

Is there a reason for this, or is this a bug?

---

### Post by EchoBeach on 2007-11-04
Are you saying that the names are being reported as lower case or the system is actively renaming them?  What OS(es) are you using?

---

### Post by bingoUV on 2007-11-04
Maybe you know this already, but on FAT it does not matter whether the name is in capital or lower case.

---

### Post by grineyfase on 2007-11-04
I'm not sure if they're being actively changed or it's just displaying as such, but I use Vista and Ubuntu. However, I've not used Vista since I installed Ubuntu (post-Ubuntu install the files displayed fine), so the reason as to why it's starting to do it now eludes me.

It shows up through Rhythmbox, LinuxDC++, and Nautilus, and it's a real pain when DC++ has to rehash through thousands of files when they haven't actually changed.

---

### Post by nick_h on 2007-11-04
Add shortname=mixed to the list of mount options for the partition in your /etc/fstab file.

---

