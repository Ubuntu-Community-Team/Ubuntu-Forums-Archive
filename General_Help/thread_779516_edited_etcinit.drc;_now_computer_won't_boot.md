---
title: "edited /etc/init.d/rc; now computer won't boot"
date: 2008-05-02
forum: General Help
---

### Post by tiodan on 2008-05-02
i edited /etc/init.d/rc by uncommenting "debug=echo", and now when i reboot the computer won't boot correctly. the last few things i see are:

/etc/rc2.d/S99rmnologin start

Ubuntu 7.04 (none) tty1

(none) login:

at that point, i can login either as my regular user or as root, but my whole filesystem is mounted read-only, so i can't undo the edit to /etc/init.d/rc.

please help,

thanks,

dan

---

### Post by Zimmer on 2008-05-02
perhaps you could pop in the live cd and get a root session & edit the file from there

---

