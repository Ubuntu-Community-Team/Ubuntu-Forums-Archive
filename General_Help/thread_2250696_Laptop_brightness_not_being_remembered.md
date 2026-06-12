---
title: "Laptop brightness not being remembered"
date: 2014-10-30
forum: General Help
---

### Post by vasa1 on 2014-10-30
[Fix Brightness Getting Reset (To A Very Low Value Or Maximum) On Reboot In Ubuntu]("http://www.webupd8.org/2014/10/fix-brightness-getting-reset-to-very.html")> If your laptop's brightness is not saved and is set to a very low value or to maximum, each time you reboot and / or when you log out, read on for a fix / workaround.I didn't have this problem in 14.04 (and earlier) but I'm seeing it after moving to 14.10.

Anyone else seeing this? In my case, the brightness rises to max on log in, log out, and boot up. Setting it the way I like manually each time isn't difficult and I'm hesitant to make the changes suggested in the link.

---

### Post by bapoumba on 2014-11-01
Well, I do not have this issue. The fix looks ok to me as it involves creating a conf file for upstart in /etc/init that you can remove if you are not happy with it. Maybe someone else who knows better can point at drawbacks ?

---

