---
title: "Boot time - what's going on?"
date: 2007-02-16
forum: General Help
---

### Post by AusIV4 on 2007-02-16
I'm trying to do some troubleshooting with regard to programs starting up when my system boots. This used to be a lot easier prior to Edgy, as the startup screen would tell you exactly what it was doing.

Now I've got some startup processes that's hanging for a fairly long time (a minute or two), but I have no idea what it is or how to find out. Is there anything I can do to get a list of things as they start?

---

### Post by till_nur_till on 2007-02-16
If you remove quiet and/or splash in "/boot/grub/menu.lst" for your boot-option it should show all the information.

---

