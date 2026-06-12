---
title: "How to uninstall KDE and KDE4?"
date: 2008-05-24
forum: General Help
---

### Post by roytang on 2008-05-24
Hi,

I have both gnome and kde installed (the original installation disk I used was Kubuntu Edgy) I also have kde4 installed (I installed it before Hardy was released)

Is there an easy way to uninstall all the KDE-related packages? I've been a primary Gnome user for months now and I want to recover some disk space.

Thanks!

Roy

---

### Post by RATM_Owns on 2008-05-24
```
sudo aptitude purge kubuntu-desktop kubuntu-kde4-desktop
```
Removes KDE 3.5 and KDE 4.
kubuntu-desktop is the 3.5 and kubuntu-kde4-desktop is KDE 4.

---

### Post by ibuclaw on 2008-05-24
> **RATM_Owns said:**
> ```
sudo aptitude purge kubuntu-desktop kubuntu-kde4-desktop
```
Removes KDE 3.5 and KDE 4.
kubuntu-desktop is the 3.5 and kubuntu-kde4-desktop is KDE 4.

Following up on that...

```

sudo apt-get autoremove
sudo apt-get install -f

```
Clears out anything installed that's left behind from the removal.

And there are two useful packages to handle excess manual and library content too.

```
sudo apt-get install localepurge gtkorphan
```
localepurge is just ran as **sudo localepurge** in the commandline, and gtkorphan is in your gnome menu.

Depending on the time since you last installed Ubuntu, you could free up to 100MB of clutter which those two tools.

Regards
Iain

---

### Post by roytang on 2008-05-26
Thanks guys!

---

