---
title: "USB Clone Problem"
date: 2018-12-13
forum: General Help
---

### Post by bilkay on 2018-12-13
I'm currently running a desktop PC with Ubuntu 16.04 installed on a 32 GB USB stick. I intended this to be temporary, but found it to be more reliable than running from a HDD. I wanted to clone the USB (/dev/sdc) onto another 32 GB USB stick so I'd have a backup in case the USB failed. I ran dd if=/dev/sdc of=/dev/sde and the resultant "clone" looks exactly like the source, but when I try to boot from it, it boots into an (initramfs) prompt.

Any ideas?

---

### Post by TheFu on 2018-12-13
Different UUIDs?   blkid and the contents of the /etc/fstab 
Just a guess.

Also, when using dd, it is best to use a blocksize to make it faster and to sync any changes. Buffering can leave bits in RAM that are needed on the storage media.

---

### Post by bilkay on 2018-12-13
Oops! Forgot to mention that after doing the dd, did an rsync -aHx --delete. When I recloned the thumbdrive without doing the rsync, it worked fine. I don't understand how rsync would break it.

---

### Post by TheFu on 2018-12-13
If the UUIDs didn't change, then when you connect two USB devices, the OS can get confused if the UUID is used in the mount.

---

