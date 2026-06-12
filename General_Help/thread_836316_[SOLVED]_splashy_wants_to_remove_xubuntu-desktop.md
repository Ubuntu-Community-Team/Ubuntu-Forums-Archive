---
title: "[SOLVED] splashy wants to remove xubuntu-desktop"
date: 2008-06-21
forum: General Help
---

### Post by x1a4 on 2008-06-21
Hi,

I want to install splashy (formally bootsplash) but it wants to remove

xubuntu-artwork
xubuntu-artwork-usplash
xubuntu-desktop

The usplash artwork I have no problem with since I don't use usplash but the Xubuntu artwork and of course the xubuntu-dekstop packages I need.  Save installing from source, is there a way to install splashy without breaking xubuntu-desktop or xubuntu-artwork?

I'm using aptitude for package management.

Thank you.

---

### Post by Nepherte on 2008-06-21
ubuntu-desktop is more like a virtual package. If one of those packages, like gedit gets removed, the virtual package ubuntu-desktop gets removed as well because gedit is part of that virtual package. That doesn't mean every package from ubuntu-desktop gets removed, only gedit in our example.

---

### Post by x1a4 on 2008-06-21
Thanks.  I got splashy installed without any damage, only now GDM will not start when I use it.  Oh well, I'm sure I'll figure it out.

---

