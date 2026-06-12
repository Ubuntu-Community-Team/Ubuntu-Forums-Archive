---
title: "How do I skip the disk check after an &quot;unclean shutdown&quot;"
date: 2008-06-24
forum: General Help
---

### Post by Manad on 2008-06-24
About once a week, Kubuntu fails to shut down properly. After X stops, I see some scripts running in command line (etc/local or something). I then switch to a console login (ALT+CTRL+Fx) and issue the shutdown/reboot command, which works.

The problem is that the next time I boot Kubuntu, it says "unclean shutdown" and spends 15 minutes checking the drives.

I was wondering if there's a way to stop this disk check after an unclean shutdown. I don't care about data corruption, it's more important that I be able to use my computer immediately without waiting 15m when I need to.

Before you ask, I did try pressing ESC. It doesn't do anything.
I think it only lets you skip routine disk checks and this doesn't qualify as one.

Thanks.

---

### Post by lisati on 2008-06-24
Apart from the potential annoyance of having to wait, would it really hurt to have the disk checks run to completion?

---

### Post by Manad on 2008-06-24
It's not a potential annoyance. It's a real annoyance with the potential to make me miss a movie at the theater or a train or worse one day.

Checking the drive is pointless because there's nothing of importance on it. I would very much like to keep my 15 minutes than deal with it.

---

### Post by sdennie on 2008-06-25
Did you partition your disks as ext2?  With ext3, an unclean shutdown doesn't automatically trigger a disk check.  I wasn't able to find an "official" guide to for converting ext2 to ext3 but, this post may help: [http://ubuntuforums.org/showthread.php?t=193103](http://ubuntuforums.org/showthread.php?t=193103)

---

