---
title: "SSD Optimization: should I config something on a fresh install?"
date: 2013-11-10
forum: General Help
---

### Post by Stupid_Guy on 2013-11-10
Hello all,
I have recently installed Saucy Salamander on my ASUS U36SG after upgrading my machine to SSD.
I've found multiple posts around telling how to tweak ubuntu for best performance and SSD lifetime,
so my question is: should I do something for my SSD or the default installation is ok?

Thank you in advance!
):P

---

### Post by oldfred on 2013-11-10
Similar discussion in this thread.

[http://ubuntuforums.org/showthread.php?t=2186323](http://ubuntuforums.org/showthread.php?t=2186323)

---

### Post by Stupid_Guy on 2013-11-11
Hello olfred and thank you for your reply.
Found something interesting [here]("http://blog.neutrino.es/2013/howto-properly-activate-trim-for-your-ssd-on-linux-fstrim-lvm-and-dmcrypt/") 
So it seems that by default there isn't any specific setting for ssd.

---

### Post by oldfred on 2013-11-11
I originally used discard but changed to a daily cron task with fstrim. You do have to have AHCI mode on.

 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

---

