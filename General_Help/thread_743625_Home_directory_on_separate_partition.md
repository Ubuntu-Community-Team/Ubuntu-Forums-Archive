---
title: "Home directory on separate partition"
date: 2008-04-02
forum: General Help
---

### Post by andrewc6l on 2008-04-02
Any way that copies the files over is good. I suspect you're seeing different methods because:
 - cp won't preserve ownership and rights, mv will (if you do it as root), rsync will too
 - mv won't preserve device files, cpio will
... etc. You might want to do a ls -alR /home > /tmp/save-me before you do the transfer, and keep that file so you can verify that the permissions / ownership is correct.

You'll need to modify fstab if you want the /home filesystem to be mounted on boot. (You probably do.) Otherwise, after every boot you'll have to mount /dev/hda2 /home

---

