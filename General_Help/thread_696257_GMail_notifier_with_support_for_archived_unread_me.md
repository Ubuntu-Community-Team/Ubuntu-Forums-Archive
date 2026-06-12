---
title: "GMail notifier with support for archived unread messages."
date: 2008-02-13
forum: General Help
---

### Post by solarwind on 2008-02-13
Hey all, is there a GMail notifier for Linux that sits in the system tray that **has support for unread messages that are archived**? I have several filters set up that label and archive unread messages so they don't appear in my inbox. The firefox GMail extension works very well for this but I can't find something that sits in the system tray. Anyone know of something?

---

### Post by linuxwizard on 2008-02-14
Look at ChechGmail it may work for you. Can be installed through repo.

[http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

---

### Post by solarwind on 2008-02-14
> **linuxwizard said:**
> Look at ChechGmail it may work for you. Can be installed through repo.

[http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

Thanks! This works very well but you have to add all your labels so it wont check for normal archived unread messages. However, I did find libgmail - [http://libgmail.sourceforge.net/](http://libgmail.sourceforge.net/) - a python library for GMail. I made a simple checker that works always, even for archived unread messages. I'll need to make an applet out of this. **Is there a way to make a python kicker applet?**

---

### Post by linuxwizard on 2008-02-14
You're Welcome I just thought CheckGmail might work for you for what you were looking for. I have no knowledge of making an applet or working with python.

---

