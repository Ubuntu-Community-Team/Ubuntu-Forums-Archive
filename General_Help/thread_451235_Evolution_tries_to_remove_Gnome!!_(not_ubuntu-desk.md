---
title: "Evolution tries to remove Gnome!! (not ubuntu-desktop)"
date: 2007-05-22
forum: General Help
---

### Post by mahy on 2007-05-22
This is what happened on a computer belonging to a friend of mine. See the attached picture for details. I know it's in Slovak language, but it should be fairly self-explanatory. Either i'm blind or Synaptic forces the user to remove Gnome as well as Evolution. After the reboot, the X wouldn't start.

---

### Post by PartisanEntity on 2007-05-22
Boze, nie dobre

---

### Post by Lucifiel on 2007-05-22
Ouch... btw, what theme is your friend running?

---

### Post by mahy on 2007-05-22
> **Lucifiel said:**
> Ouch... btw, what theme is your friend running?

Not sure, i'll ask him..

---

### Post by prizrak on 2007-05-22
That is more than normal, Evolution is part of Gnome and provides alot of back end services to it.

---

### Post by mahy on 2007-05-22
> **prizrak said:**
> That is more than normal, Evolution is part of Gnome and provides alot of back end services to it.

No, it's not normal. It doesn't happen on most installations. It never happened to me.

BTW, someone asked about the theme on that screenshot. It's Beryl SolidLine.

---

### Post by bapoumba on 2007-05-22
Thread moved to "General Help".

BTW, what was your friend trying to remove ? Ubuntu-desktop depends on evolution, and its quite surprising that "just" gnome be removed.

---

### Post by Zootropo on 2007-05-22
Don't bother with my answer, I didn't read the title.

---

### Post by mahy on 2007-05-22
> **Zootropo said:**
> ubuntu-desktop is a pseduo package which defines which applications are installed by default.
You are not going to lose your desktop uninstalling it, it's being uninstalled because when you remove evolution you don't have the list of per default applications.
You can remove it safely.

Don't wanna be mean to you, but: Have you at least glanced at the screenshot in my original post?? There's nothing about ubuntu-desktop being a problem. It's also mentioned in the title of this thread. I don't care about ubuntu-desktop... ](*,)  *TIRED*

---

### Post by mahy on 2007-05-22
> **bapoumba said:**
> Thread moved to "General Help".

BTW, what was your friend trying to remove ? Ubuntu-desktop depends on evolution, and its quite surprising that "just" gnome be removed.

Ubuntu is full of surprises. :confused: That's what i wanna sort out. He wants to get rid of Evolution.

---

### Post by bapoumba on 2007-05-22
Has he previously removed other packages that where a dependence for ubuntu-desktop?
He can find out with:
```
aptitude show ubuntu-desktop
```
That will tell if ubuntu-desktop is still installed or not.

---

