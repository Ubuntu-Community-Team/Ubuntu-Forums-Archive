---
title: "Virtual Consoles"
date: 2008-02-21
forum: General Help
---

### Post by jagem on 2008-02-21
Does anybody know how to change the quantity of the virtual consoles in Ubuntu? I used to do this in /etc/inittab in other distributions. Thanks.

---

### Post by mali2297 on 2008-02-21
Look in the directory /etc/event.d/.

For example, if you want to exclude tty6, then rename the corresponding file.
```

cd /etc/event.d
sudo mv tty6 tty6.bak

```

---

### Post by jagem on 2008-02-22
Thanks mali, i didn´t knew where to look.

---

### Post by fiprojects on 2008-02-23
How can I get a shell on my virtual consoles? I've tried CTRL+ALT+F1 for example and my screen goes blank - so do all the others until I get to F7 and my Gnome comes back.

---

### Post by mali2297 on 2008-02-23
> **fiprojects said:**
> How can I get a shell on my virtual consoles? I've tried CTRL+ALT+F1 for example and my screen goes blank - so do all the others until I get to F7 and my Gnome comes back.

There is a bug in Gutsy, see
[http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454)

---

