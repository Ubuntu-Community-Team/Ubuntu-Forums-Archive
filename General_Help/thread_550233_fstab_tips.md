---
title: "fstab tips"
date: 2007-09-13
forum: General Help
---

### Post by Geronimo on 2007-09-13
My system:Ubuntu 7.04, two users, "paolo" (me as administrator uid:1000) and "toldo" (normal user uid;1001)

I would like to load at boot an ntfs partition but only for me ("paolo") and prohibit "toldo".
This seems to work (I don't know if is the best way)
UUID=D46A82076A81E698 /media/sda2 ntfs-3g defaults,umask=007,gid=1000,locale=it_IT.UTF-8 0 0

Now I would like to mount one subdirectory of that ntfs partition only for "toldo"
I tryed
/dev/sda2/Users/toldo /media/toldo ntfs-3g defaults,locale=it_IT.UTF-8 0 0
but without success (because /dev/sda2/Users/toldo isn't block device)

Anyone know how to do?

Another question about mounting in fstab a samba directory on the network.
Using that line
//192.168.1.50/Document /media/Server1	smbfs	defaults,umask=007,gid=1000,username=xxx,password=yyy	0	0
work but the system mount that shared folder for all the users and not only for me ("paolo") as the ntfs line over. Why?

Many tanks

---

