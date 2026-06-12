---
title: "Group Permissions, access denied...."
date: 2005-09-13
forum: General Help
---

### Post by Ride Jib on 2005-09-13
I wasn't too sure where this post belonged, but figured this was as good a place as any....

I have a second hard drive on my system, ext3, which is slave. I can view everything on the drive no problem. The problem I have is this used to be on a Fedora box, and file owner is root, and group is "friends." I created the new group "friends" on my Ubuntu machine (where the drive now is) and added myself to it. Permission denied. I then figured the gid were different so i sudo chown -R root:friends /dir and tried it again. No dice. I also tried chmod -R 770 to make sure I the group had enough permission. Again, no dice.

Anyone with any ideas? If I chgrp to my username (my default group, it does allow me access). I'm stumped.

---

### Post by Ride Jib on 2005-09-13
ok, so rebooting the computer fixed the problem, but I would still like to know why, or an alternative to having to reboot the system? (I am command line friendly :))

---

### Post by umproko5 on 2005-10-20
[QUOTE=Ride Jib]ok, so rebooting the computer fixed the problem, but I would still like to know why, or an alternative to having to reboot the system? (I am command line friendly :))[/QUOTE]

I too would like to know why a reboot solves this problem/issue. I noticed the same thing in Gentoo.
.... I hate rebooting ....

---

### Post by Alexander Kirillov on 2005-10-20
[QUOTE=Ride Jib]ok, so rebooting the computer fixed the problem, but I would still like to know why, or an alternative to having to reboot the system? (I am command line friendly :))[/QUOTE]
I do not quite understand this, but my guess is that unmounting/remounting the disk would also do the trick.

---

