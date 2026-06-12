---
title: "All menus appear behind windows"
date: 2006-12-12
forum: General Help
---

### Post by TheGilmanator on 2006-12-12
I'm using Edgy, Gnome, with Beryl 0.1.3 and all of my menus and dropdown boxes are appearing behind my windows.

Everything was working fine last night when I shut down my PC, but when I started it up today the menus were all hiding on me!

It has to be something with my XGL session or with Beryl, because when I log in to a plain-old Gnome session without the eye candy the problem doesn't occur.

Has anyone seen this?

---

### Post by TheGilmanator on 2006-12-12
I found a very dirty, but workable solution.

```
sudo apt-get remove beryl
sudo apt-get remove emerald-themes
```

Restarted X with CTL + ALT + BACKSPACE

Logged back into my XGL Gnome session

```
sudo apt-get install beryl
sudo apt-get install emerald-themes
```

All of my configuration settings were still intact, but the menus were no longer popping up in the background. ](*,)

---

### Post by russo.mic on 2006-12-17
Wow,

A dirty solution, but an effective one.

Thanks friend.

---

### Post by mcduck on 2006-12-17
That's a small bug that sometimes happens with Beryl. But all you need to do is restart Beryl, and you can do that by clicking the Beryl icon in Notification Area and selecting 'Reload Window Manager'.

---

### Post by coldstatue on 2007-05-24
I used to have this problem, but I have a new version of it. i am using Feisty with beryl.  My menus are ok, but whenever a new window opens up, like a new even in sunbird, or the password window for synaptic, it pops up behind the main app. When I click on the main app, the window appears. Any ideas? Restarting beryl doesn't work.

---

### Post by afrodwarf on 2007-06-08
> **coldstatue said:**
> I used to have this problem, but I have a new version of it. i am using Feisty with beryl.  My menus are ok, but whenever a new window opens up, like a new even in sunbird, or the password window for synaptic, it pops up behind the main app. When I click on the main app, the window appears. Any ideas? Restarting beryl doesn't work.

I have this same issue with the password window in Synaptic, i cant get Synaptic starting and my window kind of freezes with a diffuse frame of the password window, any sollutions for this issue?
I have tryied turning of the "focus stealing prevention" with no luck.

:(

---

