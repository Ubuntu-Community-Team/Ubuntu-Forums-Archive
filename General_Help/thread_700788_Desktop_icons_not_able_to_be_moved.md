---
title: "Desktop icons not able to be moved"
date: 2008-02-18
forum: General Help
---

### Post by tonywhelan on 2008-02-18
Inadvertently clicked "Clean up by name" on right-click menu of desktop. Icons all lined up in alpha order, naturally.

Tried to drag them back to the positions on the desktop that I prefer. No dice. Icons dragged just pop right back to where they came from.

I can't re-arrange these icons (some launchers, some links) at all. It is not a showstopper but is an irritation.

Forum and Google searches haven't shown an identical report yet, and I can't find the (gnome?)  settings that would control this - gconf-editor doesn't seem to have anything like that.

Any thoughts welcome.

---

### Post by Yellow Pasque on 2008-02-18
maybe open gconf-editor and try looking in /apps/nautilus?

---

### Post by tonywhelan on 2008-02-18
> **Temüjin said:**
> maybe open gconf-editor and try looking in /apps/nautilus?

Thanks, but I have already looked and can't see any setting there that would account for this. But I'll have another look soon just in case there is something buried there .

---

### Post by Tenken on 2008-02-18
Try right-clicking your desktop and unchecking "Keep Aligned", it automatically got check after I cleaned mine up by name.

---

### Post by tonywhelan on 2008-02-18
> **Tenken said:**
> Try right-clicking your desktop and unchecking "Keep Aligned", it automatically got check after I cleaned mine up by name.

Thanks, but I've been through that too. I think there is some sort of corruption somewhere.

But I plan to do a new build in a few weeks so I can live with it in the meantime.

---

### Post by Anduu on 2008-02-18
Obligatory silly question time...have you tried restarting yet?

---

### Post by tonywhelan on 2008-02-19
> **Anduu said:**
> Obligatory silly question time...have you tried restarting yet?

Yes, restarted several times. I started a Gnome session, an xwindows session, and a Gnome safe mode session at various times but all the same result. (I really don't know the difference between them, but hey it seemed worth a try).

I found some XML files in ~/.nautilus/metafiles/  and selected one with a recent timestamp  that looked to have the desktop icon details in it.

I edited the icon coordinates for the entries and saved the file, then restarted the desktop with "killall nautilus". 

The icons then displayed in their new positions, which is fine for now. I still can't move them by dragging though.

I think there is some corruption on my build but it can wait till next rebuild as everything else seems to be working as normal.

Funnily enough, I have always wanted a setting that locked the desktop icons so they couldn't wander about. Now I have that, but don't know how :)

---

