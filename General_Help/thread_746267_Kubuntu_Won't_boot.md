---
title: "Kubuntu Won't boot"
date: 2008-04-05
forum: General Help
---

### Post by Zophixan on 2008-04-05
Heya, just did a full update last night, and now kubuntu won't boot, it just goes to a command line, asking me to log in! I'm new to linux, so I don't know how I can access the logs, I can see the partition in windows though. Thanks in adance!
Just tried start x, and I get, failed to open frambuffer device, fatal io error on x server. no screens found, screens found but non have a usable configuration etc. Tried reinstalling drivers, and kde, but no avail :-(

---

### Post by TeoBigusGeekus on 2008-04-05
When you enter your grub menu, what options do you have?

---

### Post by pointone on 2008-04-05
Log in at the command line and run the following command:

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

This will regenerate your xorg.conf file and hopefully allow you to start X again.

---

