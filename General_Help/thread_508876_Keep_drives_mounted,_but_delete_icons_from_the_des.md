---
title: "Keep drives mounted, but delete icons from the desktop... how?"
date: 2007-07-24
forum: General Help
---

### Post by exaulz on 2007-07-24
Hey guys. I want to keep my drives mounted (Windows Vista partition, iPod, and USB stick), but I don't want their icons on my desktop. Is there anyway to just delete the icons, NOT unmount the drives? And, would there be any way to restore the icons / re-add them? If so, how?

Extremely sorry if this has been asked before, or is posted in the wrong section. I installed Ubuntu (again) today and I'm having a blast.

Thanks in advance.

---

### Post by bodhi.zazen on 2007-07-24
You can either mount them in /mnt rather then /media (update /etc/fstab)

Or

[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

### Post by exaulz on 2007-07-24
Thank you so much! 

*gives you a teaspoon of sugar for your coffee*

=].

---

### Post by dando80 on 2007-07-28
You can also toggle the apps->nautilus->desktop->volumes_visible flag in gconf editor. Applications->System Tools->Configuration Editor

---

### Post by bodhi.zazen on 2007-07-28
> **dando80 said:**
> You can also toggle the apps->nautilus->desktop->volumes_visible flag in gconf editor. Applications->System Tools->Configuration Editor

thanks ...

FYI, although not obvious, this is the same information as is in the link I posted. The advantage of the link is that there are screen shots with a short but very nice walk through. You *might* consider the same link in the future is all I am suggesting (although I could also have explained it better).

---

### Post by strabes on 2007-07-28
Does gnome have a panel applet to show mounted drives? That's what I use in KDE; it's really useful.

---

### Post by bodhi.zazen on 2007-07-28
There is (but I am not sure how well it works i do not use it)

[img]http://www.gnome.org/~jamesh/images/drive-mount.png[/img]

---

