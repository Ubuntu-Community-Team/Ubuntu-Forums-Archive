---
title: "cannot ever see boot splash?"
date: 2008-04-20
forum: General Help
---

### Post by irunwithknives on 2008-04-20
when I boot my computer, instead of showing the boot splash, it says "out of range" in my monitors default dialouge, yet boots properly.  I still kinda like the boot splash, so is there any way to make it show?

---

### Post by TeoBigusGeekus on 2008-04-20
Go to system->administration->start up manager. Is the show boot splash button checked?

---

### Post by irunwithknives on 2008-04-22
there actually is no startup manager...

---

### Post by dcstar on 2008-04-23
> **irunwithknives said:**
> when I boot my computer, instead of showing the boot splash, it says "out of range" in my monitors default dialouge, yet boots properly.  I still kinda like the boot splash, so is there any way to make it show?

Try this:

In a terminal, edit the first file to your current screen res, and then reboot after the second command:

```
sudo gedit /etc/usplash.conf
sudo update-initramfs -u
```

---

### Post by erginemr on 2008-04-23
> **dcstar said:**
> Try this:

In a terminal, edit the first file to your current screen res, and then reboot after the second command:

```
sudo gedit /etc/usplash.conf
sudo update-initramfs -u
```

+1 to that.

For a more verbose explanation and howto:
*[http://ubuntuforums.org/showthread.php?t=700673](http://ubuntuforums.org/showthread.php?t=700673)*

---

