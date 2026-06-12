---
title: "How to configure closing lid options in 22.04.2"
date: 2023-05-14
forum: General Help
---

### Post by fahrbach on 2023-05-14
I don't show this option under power options.  What's funny is closing the lid does nothing which is what I want!  But no pull down menu for suspend, hibernate, etc.

---

### Post by TheFu on 2023-05-14
/etc/systemd/logind.conf has multiple lid configuration options that systemd honors.

```
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=suspend
#HandleLidSwitchExternalPower=suspend
#HandleLidSwitchDocked=ignore
#HandleRebootKey=reboot
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#RebootKeyIgnoreInhibited=no
```
are some of the default options.  The manpage for that file explains what each means and valid values.

---

### Post by fahrbach on 2023-05-14
thank you!  Funny thing is supposedly the default is suspend!  Does not work on my HP which is just fine.

---

### Post by TheFu on 2023-05-15
> **fahrbach said:**
> thank you!  Funny thing is supposedly the default is suspend!  Does not work on my HP which is just fine.

Systemd settings may be different than what some desktop environment settings do.  IDK. I don't use DEs like Gnome/KDE/Mate.

For any settings specific to a DE, I'd look for the User Guide for that DE.  Sometimes these are called "desktop guides" too. So, if I were running Xubuntu 22.04, I'd look for the "22.04 Xubuntu Desktop guide" using a web search.  Found this website: [https://xubuntu.org/help/](https://xubuntu.org/help/)  That's just an example.  Same for lubuntu or gnome or mate or ... whatever.

---

