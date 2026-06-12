---
title: "Kubuntu login screen"
date: 2008-01-04
forum: General Help
---

### Post by tiger.woods on 2008-01-04
I just upgraded to 7.10 and when I login I still see a Kubuntu login screen. I'm really wanting to just have gnome as the login screen.

So I thought I would uninstall Kubuntu-Desktop and it isn't installed? Is there a way to force an install of Gnome?

Thanks,

---

### Post by PeterJS on 2008-01-04
I think what you're saying is that when you start your system up you login through KDM, but are using the gnome desktop and want to switch to login with GDM?

To switch login managers:
```

sudo dkpg-reconfigure gdm

```
When given the option select gdm and you're done.

---

### Post by tiger.woods on 2008-01-04
Exactly! right on the money... thanks. :)

---

### Post by tiger.woods on 2008-01-04
Another quick question regarding the previously installed packages and my recent upgrade to 7.10.

In the "Other" category of application I have a boatload of apps without icons that just seemed to have been dumped there, they appear to be legit shortcuts to the applications.

Is there a way to reset the menus?

---

### Post by PeterJS on 2008-01-04
I don't think there's a way to reset the menus, they should always be as up to date as the system can manage, what kind of stuff is in there?

---

### Post by tiger.woods on 2008-01-04
A-Z apps...

Some strange ones... Cache, Colors, CGI Scripts..., Fonts, IO-Ports, Memory, Panels, etc...

---

### Post by PeterJS on 2008-01-04
So I just loaded up gnome to take a look, and what'cha know I've got the same stuff in there, looks mostly like KDE configuration modules. You can go to System > Prefences >Main menu and hide all of them, or you could just ignore them, or you could go on a hunt to root out and remove the remaining KDE components on your system. Psychocats  has a decent guide to getting rid of KDE:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by tiger.woods on 2008-01-04
2 for 2 ... much appreciated, thanks again.

TW,

---

