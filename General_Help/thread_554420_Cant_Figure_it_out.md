---
title: "Cant Figure it out"
date: 2007-09-19
forum: General Help
---

### Post by RetroDemon on 2007-09-19
Installing java, got to the update point, and it fails, but its sitting there waiting to be installed still. I have a blip that says 2 updates avaible but it will not download.  HELP!?!?!

---

### Post by dcstar on 2007-09-19
> **RetroDemon said:**
> Installing java, got to the update point, and it fails, but its sitting there waiting to be installed still. I have a blip that says 2 updates avaible but it will not download.  HELP!?!?!

When you install any of the Java packages you have to accept the licence conditions, and if it doesn't ask (for some reason), then it just won't install even though the process seems to complete ok.

Do this in a terminal, set it to Gnome and Medium and try the Java install again:
```
sudo dpkg-reconfigure debconf
```

---

### Post by buixuanduong1983 on 2007-09-19
I never instal Java, so I'm not sure what's wrong with it, but for a general ideal:

- Stop the install, then try again
- If still not work: restart your computer and try again
- Maybe the network: see if you can load a website...
- Sound stupid, but if you have a proxy, I think you have to config somehow for the installer to use it.

---

### Post by RetroDemon on 2007-09-19
ok when i did that, i selected medium and it sent me back to the terminal, and is waiting for a command

---

