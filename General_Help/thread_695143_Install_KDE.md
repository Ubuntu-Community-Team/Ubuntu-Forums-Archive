---
title: "Install KDE?"
date: 2008-02-12
forum: General Help
---

### Post by nosushi4you on 2008-02-12
I'm pretty new to Linux, so I want to try my hand at a few of the desktop environments. So, I want to install KDE. Just a few questions though, if I already have my video card configured, will I have to re-configure it for KDE, or will it work without any modifications? Also, if I don't like KDE, how easy is it to uninstall? Do I have to download anything besides for the "sudo aptitude kubuntu desktop" thing? Will it affect GNOME in anyway? Thanks for any answers you are able to provide.

---

### Post by taurus on 2008-02-12
1.  No, you don't have to reconfigure your X server again if you choose to run KDE.

2.  You can remove KDE by using this guide, [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome).

3.  The command to install KDE is 

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

4.  No, it won't effect Gnome if you install KDE.  However, you can run KDE apps while you are in Gnome and vice versa.

---

### Post by dbzkid on 2008-02-12
well you can do that but its seously a pain, i hated it, just go to synaptic and search for KDE and there u go, it will still say ubuntu and u will beable to choose between gnome and kde, just go to the session menu at the login screen, its verry easy to uninstall just go to synaptic and search kde and choose to uninstall

---

