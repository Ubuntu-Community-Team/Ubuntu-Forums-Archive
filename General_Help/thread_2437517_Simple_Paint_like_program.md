---
title: "Simple Paint like program"
date: 2020-02-25
forum: General Help
---

### Post by Philip_Edwards on 2020-02-25
Hi, Any advice?
I need a simple Paint program. I've tried Drawing and GNU Paint. With both of them I haven't found a way to select an area and crop unless I'm missing something really obvious.

My needs are simple. 

Phil

---

### Post by ajgreeny on 2020-02-25
Have a look at **mtpaint**; it's a bit like the simple Microsoft paint application as far as I can remember, though I've not used either for a very long time.

If you really want a gnome application try **gthumb** as well.

Both are in the normal repos so easy to install.

---

### Post by GhX6GZMB on 2020-02-25
Kolourpaint. It's an almost 1:1 to MS Paint. It's already in the repo.

---

### Post by Philip_Edwards on 2020-02-25
Thanks. Found and installed.
Phil

---

### Post by cmcanulty on 2020-02-25
pinta is in the repositories and quite easy to use

[ATTACH=CONFIG]285095[/ATTACH]

---

### Post by mörgæs on 2020-02-25
> **Philip_Edwards said:**
> Thanks. Found and installed.
Phil

Good, if this solves the problem please mark the thread so.
It will help other users.

---

### Post by Dennis N on 2020-02-25
> **Philip_Edwards said:**
> Thanks. Found and installed.
Phil
Based on posting sequence, I assume this refers to [kolourpaint]("https://kde.org/applications/graphics/org.kde.kolourpaint")? Be aware it's a KDE application and depends on a different group of libraries than an application designed for Gnome, and that all those extra libraries have to be installed. Now,  we have snap or flatpak applications that keep the supporting libraries (or runtimes, as they are called) segregated from the rest of the system rather than intermixed - a fact that makes it easy to clean them out if you change your mind. Kolourpaint has both a snap version and a flatpak version. I would use either one of those instead of the apt version. But if you installed from the Ubuntu repository, it's too late to take advantage of this.

Note: using apt to install kolourpaint on my Ubuntu system requires 97 new packages! See what's needed with **apt install -s kolourpaint**

---

### Post by GhX6GZMB on 2020-02-25
> **Dennis N said:**
> Based on posting sequence, I assume this refers to [kolourpaint]("https://kde.org/applications/graphics/org.kde.kolourpaint")? Be aware it's a KDE application and depends on a different group of libraries than an application designed for Gnome, and that all those extra libraries have to be installed. Now,  we have snap or flatpak applications that keep the supporting libraries (or runtimes, as they are called) segregated from the rest of the system rather than intermixed - a fact that makes it easy to clean them out if you change your mind. Kolourpaint has both a snap version and a flatpak version. I would use either one of those instead of the apt version. But if you installed from the Ubuntu repository, it's too late to take advantage of this.

Note: using apt to install kolourpaint on my Ubuntu system requires 97 new packages! See what's needed with **apt install -s kolourpaint**

Your comment is bit over the top. Kolourpaint has 22 dependencies, all of them to libkf5* or libqt5*. I run Lubuntu, so I don't know if these are present on a Gnome  system (probably not). The rest of the required files/packages are screen icons for Kolourpaint.

I find Kolourpaint fast and to the point = emulating MSPaint.

---

### Post by Dennis N on 2020-02-25
> Your comment is bit over the top. Kolourpaint has 22 dependencies
Not really - It depends on what you already have installed. I did say "on my Ubuntu system".  Lubuntu releases after 18.04 use LXQt and some KDE packages by default, so some of what is needed is already there. That explains the difference. For Lubuntu, it makes more sense.

---

### Post by 0x0840 on 2020-05-12
Try Dibuja: [https://launchpad.net/dibuja](https://launchpad.net/dibuja)
Light weight and minimal dependancies

---

