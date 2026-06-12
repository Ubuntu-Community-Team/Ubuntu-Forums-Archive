---
title: "Use KDE - how?"
date: 2007-02-07
forum: General Help
---

### Post by johann_p on 2007-02-07
How can I get KDE as an alternate desktop manager in the gdm login manager? I do not want to install "kubuntu" since I will continue to use the GNOME desktop most of the time. But I want the KDE window manager as an additional choice before I login.
How is this done?

---

### Post by etank on 2007-02-07
If you do ```
sudo aptitude install kubuntu-desktop
```then it will install KDE on your machine. You can have both Gnome and KDE at the same time and at the login screen choose which one you want to use.

I hope I was understanding you correctly.

---

### Post by johann_p on 2007-02-07
> **etank said:**
> If you do ```
sudo aptitude install kubuntu-desktop
```then it will install KDE on your machine. You can have both Gnome and KDE at the same time and at the login screen choose which one you want to use.

I hope I was understanding you correctly.


Yes that is what I want. I just am a bit cautious because last time I did this the startup logo was changed from Ubuntu to kubuntu and the login manager was changed from gdm to kdm. All attempts to get my old settings back somehow failed. 
I have no a new installation on my computer (Feisty because Edgy could not be installed on my hardware) and I would like to avoid those "side effects". 
So does the installation of kubuntu-desktop ONLY add kde as another choice to the *GDM* desktop and not change anything else?

---

### Post by allwin on 2007-02-07
I have done this on one system, and I note maybe about a 5% overlap of Gnome and KDE.  Some KDE desktop items appear on Gnome and vice versa, nothing truly unliveable.

Of interest, if you mess with Beryl, at least for me, setting themes in Aquamarine (KDE)for some reason carry over into Gnome, which is astonishingly cool.

---

