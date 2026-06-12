---
title: "Resizing of Logical volume (LVM)"
date: 2006-08-15
forum: General Help
---

### Post by Erujsoft on 2006-08-15
I added a new disk to a logical volume. Now I should make resize (resize2fs) of the volume. Before I should umount logical volume with "umount /dev/Ubuntu/root", but it doesn't let me do it (Device is busy). I installed Ubuntu 5.10 with default LVM configuration. Any suggestions? Thanks, Jure

---

### Post by louis_nichols on 2006-08-16
What kind of filesystem do you have on it? Reiser doesn't need to be unmounted. But if you have ext2/ext3, then I'm afraid you must do this from the livecd, as you can't unmount the root partition.

EDIT: question mark where needed

---

