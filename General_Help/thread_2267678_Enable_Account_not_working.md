---
title: "Enable Account not working"
date: 2015-03-03
forum: General Help
---

### Post by peridian on 2015-03-03
Hi,

I have created a second account on my ubuntu 14.04.1 (removed unity and installed lubuntu desktop) install, and tried to Enable the account from the Users and Groups screen.  It lets me enter the password, and shows as enabled.  But as soon as I close the window, if you go back in it still shows as disabled.  If I enable the account and immediately reboot, the account is disabled on the login screen.

I've enabled this finally from the command line, but I would prefer that the GUI work as well.  Any ideas?

Regards,
Rob.

---

### Post by peridian on 2015-03-03
Nevermind, I searched through the /etc/pam.d/common-* files, and discovered one of them had the pam_krb5.so line with "minimum_uid=1000" instead of 10000.  After I changed it, everything worked fine.  I'm guessing the GUI uses a different combination of the pam.d files, since the passwd command on the command line worked fine.

Regards,
Rob.

---

