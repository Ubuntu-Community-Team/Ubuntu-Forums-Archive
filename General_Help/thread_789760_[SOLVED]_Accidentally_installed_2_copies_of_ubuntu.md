---
title: "[SOLVED] Accidentally installed 2 copies of ubuntu"
date: 2008-05-10
forum: General Help
---

### Post by bartoszbr on 2008-05-10
I have had ubuntu installed in dual boot with vista for quite a while now. Today, I did system restore for vista, and thought (because I couldn't find it) that it removed my ubuntu installation. So I went to on to install another copy. To my amase, after restart, both copies showed up in the boot. How can I remove the one I just installed? Formatting that partition? If so, how?

Thanks.

---

### Post by Rocket2DMn on 2008-05-11
I suggest using the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Just make sure you are deleting the correct partitions.  You can then resize your original root partition to use the newly freed space.  If your new install of Ubuntu owns GRUB, you will need to reinstall GRUB to your original partition.  The Super Grub Disk may help with that - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Otherwise, have a look here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

