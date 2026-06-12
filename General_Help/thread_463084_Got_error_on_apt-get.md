---
title: "Got error on apt-get"
date: 2007-06-03
forum: General Help
---

### Post by mzainal on 2007-06-03
Hi,

I install VirtualBox but not finish. It keep out this error.

> E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
[IMG]http://i54.photobucket.com/albums/g114/mzainal/error.png[/IMG]

---

### Post by taurus on 2007-06-03
Open a terminal, Applications -> Accessories -> Terminal, and run these commands.

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by auryn21 on 2007-06-03
You could also try downloading the deb file directly from Virtual Box's site and installing it via right click, gdebi

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by mzainal on 2007-06-03
The problem is solve. Moderator, please close this thread.

---

