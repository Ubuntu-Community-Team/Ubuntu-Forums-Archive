---
title: "Can't run Sudo"
date: 2013-10-30
forum: General Help
---

### Post by hughmtaylor on 2013-10-30
This is a very frustrating catch 22, I can't sudo because the permissions are wrong, and I can't change the permissions without sudo.

```
sudo: /etc/sudoers is mode 0460, should be 0440
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
```

This started when I was trying to do [this fix]("http://ubuntuforums.org/showthread.php?t=1816298"). The upside is thunar opens really fast now. The downside is that I basically bricked my laptop.

"Don't ever log in to XFCE in as root" they said. "You are root, you could harm your computer" they warned. Well, I should have listened.

Apparently I can fix this by loading recovery mode through grub. Problem is I am running ubuntu on a SD card on my chromebook and I have no idea how to access grub. Any ideas or do I have to start all over again?! :*(

Any help would be greatly appreciated.

---

### Post by sisco311 on 2013-10-30
Try polkit's pkexec command:
```
pkexec chmod 0440 /etc/sudoers
```

---

