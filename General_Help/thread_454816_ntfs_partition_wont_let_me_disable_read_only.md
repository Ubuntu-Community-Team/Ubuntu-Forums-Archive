---
title: "ntfs partition wont let me disable read only"
date: 2007-05-25
forum: General Help
---

### Post by powerplayground on 2007-05-25
my other ntfs partition wont let me disable read only. Its a pain when i have to take spaces out of a program name for wine when i have to go to xp evry time, and i tried logging in as root, and it wont budge. Any way this will work, or will i just have to cope and prob just throw out Ubuntu or any Linux as a possible os :P

---

### Post by Nikron on 2007-05-25
There's a program called ntfs-config that makes it easy to add write.  Or, you can edit fstab to make it write.  Or you can umount it every time, then just do sudo ntfs-3g /dev/targetdrive and it should allow write

---

### Post by aysiu on 2007-05-25
Try this:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

