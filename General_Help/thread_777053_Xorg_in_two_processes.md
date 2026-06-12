---
title: "Xorg in two processes"
date: 2008-05-01
forum: General Help
---

### Post by magnusbb on 2008-05-01
Hello,

on my Ubuntu 8.04 system, Xorg is showing up in two processes:

root      5510  1.3 10.7 105104 97376 tty7     Ss+  09:36   1:48 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.

root      5696  0.0 10.7 105104 97376 tty7     S+   09:36   0:00 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.

They take up the same amount of memory, but only one uses CPU. Problematic is of course the memory usage, which in my case then is twice the normal size.

I've searched the forums and found another user having the same problem: he solved it by upgrading the ATI drivers to version 8.4. I have now done this, without success.

Link: [http://ubuntuforums.org/showthread.php?t=465435](http://ubuntuforums.org/showthread.php?t=465435)

Any ideas?

---

