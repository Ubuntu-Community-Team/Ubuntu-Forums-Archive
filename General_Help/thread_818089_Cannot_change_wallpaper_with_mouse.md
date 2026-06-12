---
title: "Cannot change wallpaper with mouse"
date: 2008-06-04
forum: General Help
---

### Post by sink on 2008-06-04
Hi, it seems that a recently update has a bug.

I cannot choose the wallpapers in the panel with mouse
I have to use arrow keys to choose.

also, sometimes the trash bottom on the panel bar disappear for no reason.

---

### Post by Vivaldi Gloria on 2008-06-04
> **sink said:**
> Hi, it seems that a recently update has a bug.

I cannot choose the wallpapers in the panel with mouse
I have to use arrow keys to choose.


I am suffering from this too.

---

### Post by Tyche on 2008-06-04
> **Vivaldi Gloria said:**
> I am suffering from this too.

And here I thought it was me.  OK, if it makes any difference to people, I DID notice that when I bring up Appearances my CPU use jumps to 25% or more and dogs my system.

---

### Post by maxol on 2008-06-04
Same problem here but none of my wallpapers will load and I have a black desktop.

I can select different desktop pictures in the Appearance panel using the arrow keys but the desktop remains black.

---

### Post by BigSilly on 2008-06-04
Ah! Glad I found this. I'm having the same issue too. If I hammer the mouse button on the image I want for my wallpaper in Appearance, then it will eventually select it. But that's not ideal really is it?

I have noticed (because I have the System Monitor applet on my panel) that when I select System/Preferences/Appearance, that the CPU usage goes right up to the top and slows the PC down a lot. It's got to be something to do with that yeah?

---

### Post by gail on 2008-06-04
Go to System....Administration.....Software Sources.....Updates...
click on Pre-released updates (Hardy-Proposed) click ....close

Package list will update then you will get a update notice.  Update the the packages .....should cure it.

---

### Post by BigSilly on 2008-06-04
> **gail said:**
> Go to System....Administration.....Software Sources.....Updates...
click on Pre-released updates (Hardy-Proposed) click ....close

Package list will update then you will get a update notice.  Update the the packages .....should cure it.

Really? And what should I be looking for? Any particular package that fixes it?

---

### Post by gail on 2008-06-04
Update all the packages.....there will be a bunch of them.

---

### Post by maxol on 2008-06-04
Thats over 100 packages to update on my system, seems like a bit of a sledgehammer to crack a nut.

Any ideas where the bug lies or which package I could upgrade to fix it?

---

### Post by Woormy on 2008-06-04
> **gail said:**
> Go to System....Administration.....Software Sources.....Updates...
click on Pre-released updates (Hardy-Proposed) click ....close

Package list will update then you will get a update notice.  Update the the packages .....should cure it.


This worked great for me!

You deserve a cookie!

---

### Post by Vivaldi Gloria on 2008-06-05
> **maxol said:**
> Thats over 100 packages to update on my system, seems like a bit of a sledgehammer to crack a nut.

Any ideas where the bug lies or which package I could upgrade to fix it?

Upgrade those packages whose name start with gnome or libgnome.

---

### Post by maxol on 2008-06-05
Thanks I've done that but selecting desktops in the Appearance window is still very unresponsive with the mouse.

---

### Post by sjmacko on 2008-06-05
I recently set up a machine for a friend... His eMachines with Windows Vista was very strange. He likes the feel of Ubuntu so far, but today I got the phone call that his wallpaper is gone, and so are the window buttons. I deleted all of the gnome configuration files in his user folder, but the problem persists! I logged into the account I created for his grandson, and the problem is there, as well: no window buttons, can't change theme, can't select desktop wallpaper.

I will try the prerelease updates tomorrow... Any other ideas?

Steve

---

### Post by Vivaldi Gloria on 2008-06-06
The following steps fixed the problem on 3 computers I tried.

1) Enable Hardy-Proposed repo in synaptic and refresh.

2) Then use the update manager to update the following packages:

```
libgnomeui-0
libgnomeui-common
gnome-desktop-data
gnome-about
libgnome-desktop-2
```

Now you can get rid of the Hardy-Proposed repo if you want.

---

### Post by maxol on 2008-06-08
Thanks Vivaldi Gloria, that did the trick.

---

### Post by darkaudit on 2008-06-08
> **Vivaldi Gloria said:**
> The following steps fixed the problem on 3 computers I tried.

1) Enable Hardy-Proposed repo in synaptic and refresh.

2) Then use the update manager to update the following packages:

```
libgnomeui-0
libgnomeui-common
gnome-desktop-data
gnome-about
libgnome-desktop-2
```

Now you can get rid of the Hardy-Proposed repo if you want.

That's a much better solution than just "update everything". Thank you.

---

