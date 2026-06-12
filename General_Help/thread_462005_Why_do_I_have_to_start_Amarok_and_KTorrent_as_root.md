---
title: "Why do I have to start Amarok and KTorrent as root?"
date: 2007-06-02
forum: General Help
---

### Post by loathsome on 2007-06-02
Hi,

When I try to launch Amarok I get this message> trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
kbuildsycoca running...
trying to create local folder /home/loathsome/.kde/cache-hornydawg: Permission denied
trying to create local folder /home/loathsome/.kde/cache-hornydawg: Permission denied
trying to create local folder /home/loathsome/.kde/cache-hornydawg: Permission denied
kbuildsycoca: ERROR creating database '/home/loathsome/.kde/cache-hornydawg/ksycoca'! Permission denied


When I run it as root (with «sudo») it works flawlessly. Same thing with KTorrent: > trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied
trying to create local folder /home/loathsome/.kde/share: Permission denied


Works as hell when running with root, though. What's the problem here? Thanks!

---

### Post by loathsome on 2007-06-02
Hey, wait a second! :KS

The owner of ~ /.kde was somehow root. I just ran [COLOR="DarkSlateGray"]**$ sudo chown -R loathsome ~/.kde**[/COLOR] and voilà!

Haha, problem solved.

---

