---
title: "Feisty+Gutsy - how to start X in chroot?"
date: 2007-07-18
forum: General Help
---

### Post by benanzo on 2007-07-18
I have installed Gutsy as a dual-boot with Feisty on my MacBook.  I can mount it under Feisty and chroot in but I don't have network access in the chroot (so no updates) and I'm having trouble with the X server.  I think I'm doing it all wrong.

The way that I've been chrooting:
```

sudo bash
mount -t ext3 /dev/sda4 /media/gutsy
mount -o bind /dev /media/gutsy/dev
mount -t proc none /media/gutsy/proc
chroot /media/gutsy /bin/bash

```
Now I'm in a Gutsy terminal session.  When I do:
```
sudo /etc/init.d/gdm start
```
It spawns a X session on VT9 for me to work in.  I hit CTRL - ALT - F9 to switch to gutsy and CTRL - ALT - F7 to go back to Feisty.  My question is 1) why can't I access the network in my Gutsy chroot?  I'm on wireless using NetworkManager with Feisty.  2) What is happening when I start gdm from the chrooted terminal?  It seems to affect my Feisty session.  For instance, when I log out in the gutsy session and return to Feisty, I find that it has logged out also.  And the hostname is still Feisty in the gutsy session instead of Gutsy (which is what I set it as.)  Am I going about this wrong?

This is the networking error in the gutsy chroot terminal:
```
root@feisty:/# sudo /etc/init.d/networking start
 * Configuring network interfaces...
ifup: failed to open statefile /var/run/network/ifstate: No such file or directory
[fail]
root@feisty:/#
```

Thanks!

---

