---
title: "How do I start Gnome Classic?"
date: 2012-12-28
forum: General Help
---

### Post by oxf on 2012-12-28
Just installed Quantal. Now I've added Gnome Session Fallback. How do I permanently switch to Gnome Classic. I can log out / log back in but this only works for the current session. Once I reboot it's back to Unity. I want to switch over permanently to use Gnome Classic DE

Thanks

---

### Post by MG&amp;TL on 2012-12-28
> **oxf said:**
> Just installed Quantal. Now I've added Gnome Session Fallback. How do I permanently switch to Gnome Classic. I can log out / log back in but this only works for the current session. Once I reboot it's back to Unity. I want to switch over permanently to use Gnome Classic DE

Thanks

The login manager, *lightdm* reads options for this from its configuration file /etc/lightdm.conf.

See [http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins]("http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins")

:)

---

### Post by Luigi2012SM64DS on 2012-12-28
```
sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-classic
```

---

### Post by oxf on 2012-12-29
Thank you both, that explained everything now  :)

Caitlin

---

