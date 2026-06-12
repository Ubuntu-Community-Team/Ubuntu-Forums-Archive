---
title: "[SOLVED] How to switch from KDE 4 to KDE 3.5?"
date: 2008-05-01
forum: General Help
---

### Post by vvvladut on 2008-05-01
If I remove *kubuntu-kde4-desktop* and install *kubuntu-desktop*, will that do the trick? Is there more to it? Will all the other installed applications be affected in any way?

---

### Post by Ayuthia on 2008-05-01
I am guessing that it would be fine but I have never tried it.  Why not have both on there?  I currently have 3.5 and 4 on my laptop and I am able to switch them at the login screen.

---

### Post by vvvladut on 2008-05-01
So that would mean just install *kubuntu-desktop*? How would I select which one I want to boot into?

---

### Post by brainspank on 2008-05-01
> **vvvladut said:**
> If I remove *kubuntu-kde4-desktop* and install *kubuntu-desktop*, will that do the trick? Is there more to it? Will all the other installed applications be affected in any way?

You can just install kde3 without bothering to remove kde4.  select which one you want from Sessions at login.  I just installed the 'kde' virtual group, but 'kubuntu-desktop' should work too, unless it conflicts with 'kubuntu-kde4-desktop'.  If it conflicts, it should warn you it's going to remove it.

---

### Post by der_joachim on 2008-05-02
You can install Kubuntu-desktop alongside kubuntu-desktop-kde4. Your apps will not be affected, but sharing the settings between kde3 and kde4 will be a pain in the backside.

---

### Post by vvvladut on 2008-05-02
I installed *kubuntu-desktop* and uninstalled *kubuntu-kde4-desktop*. It has worked fine, except uninstalling KDE4 didn't actually do anything, so I had to remove all KDE4 packages manually. Now I have a beautiful KDE 3.5 desktop, and it's going to stay like this.

Thanks for your help everyone.

---

### Post by tzepu on 2008-05-03
well, oddly i can not install kde 3.5.9 on my kubuntu kde4 because i just can not find the metapackage
and i just checked that i have all the repositories enabled, and i have
is adept screwed up? because i just can see my installed apps

L.E. it looks that i was just unlucky and tried to do this on a 'server down' moment
installing kubuntu-desktop works like a charm and now i have kde3 and 4 on same machine

---

### Post by vvvladut on 2008-05-03
How do I mark this as solved? It's not in the thread tools anymore...

---

### Post by Zorael on 2008-05-03
Apparently the mark-as-solved vBulletin plugin is not enabled, or so I'm told.

Anyway, to get rid of all installed packages that rhyme with kde4, do this in a terminal. No guarantees.
```
$ sudo aptitude purge ~nkde4
```

---

### Post by vvvladut on 2008-05-03
> **Zorael said:**
> Anyway, to get rid of all installed packages that rhyme with kde4, do this in a terminal. No guarantees.
```
$ sudo aptitude purge ~nkde4
```

I just ran that. It removed about 20 packages. I see no change (I rebooted), which is good. Thanks!

---

