---
title: "Increasing Ubuntu/Lubuntu Swap Space"
date: 2014-10-14
forum: General Help
---

### Post by Jorge_Calderon on 2014-10-14
I have a small amount of RAM and want to add to the swap file.  I see that this one is setup already:

Filename    Type  Size Used Priority
/dev/mapper/lubuntu--vg-swap_1          partition 5373948 21532 -1

How do I add to this?  I ran GParted and I don't see this swap file.

---

### Post by TheFu on 2014-10-14
Either you enabled LVM or encryption during installation.

The closest answer I found was here: [http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

There is a GUI for LVM management - howtogeek did an article on it. I've never used it and don't know how it works with swap ... or not.

---

