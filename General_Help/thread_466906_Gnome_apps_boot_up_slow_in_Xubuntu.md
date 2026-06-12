---
title: "Gnome apps boot up slow in Xubuntu"
date: 2007-06-07
forum: General Help
---

### Post by maniacmusician on 2007-06-07
I'm running Xubuntu on a computer at school, and all the gnome apps boot up **very** slow. This is a p4 2.4 GHz with 256MB of RAM. 

Any gnome apps, such as epiphany or the gnome Printer-config tool, or even Totem start up so slow that you can't even tell anything is happening. First, just the basic window outline pops up (see screenshot).  It gets stuck there. At this point, **the CPU is idling**, and **top shows no significant activity.** 

I'm thinking some important GTK lib might be missing but I have no idea what. If I leave the computer alone for about 15 minutes, the contents of that window finally show up, but if I click on anything in the window (like even opening the FIle menu), it gets stuck again and takes a long time to respond. 

It's not as if the CPU can't handle it, since it's idle the whole time. So I really don't know what's going on. Running the apps from the terminal doesn't produce any significant output either, except for this line:
> /bin/sh: /usr/bin/esd: not found

Any help would be appreciated,

Thanks.

---

### Post by carolinason on 2007-06-07
How's the memory doing? Are you hitting the swap area?

---

### Post by maniacmusician on 2007-06-07
Yeah, I'm 100 MBs or so into swap. But that doesn't make a difference at all. This happens even after a fresh boot when I'm not using any of the swap. like I said, I think it's a library thing...but I'm not sure what to do.

---

### Post by carolinason on 2007-06-07
If you are swapping 100MB i/o to swap, then it is going to be slow.  See if they can add a ram stick.

I doubt it is a library, if so it shouldn't run the gnome application.

---

### Post by maniacmusician on 2007-06-07
> **carolinason said:**
> If you are swapping 100MB i/o to swap, then it is going to be slow.  See if they can add a ram stick.

I doubt it is a library, if so it shouldn't run the gnome application.
well, like I said, it doesnt work even after a fresh boot when there is no swap being used. Even memory hogs like Firefox run on that machine, so I'm sure that's not the problem. It's just something about those apps...

I'm going to up the RAM to 512 tomorrow, but I dont think that will make a difference. I wish there was a way to get to the root of this problem...

---

### Post by orb9220 on 2007-06-07
Just shooting in the dark here.

1) Run apps from term for any messeges generated,
2) Is it all gnome apps in gnome desktop?
3) uninstalling and reinstalling apps to fix issue's?
4) Video driver's since the default are slow just as in xp default vga is slow?
5) create new user account and try from there.
6) Boot up in recovery mode check how apps run. Or boot into older kernel?

Sorry I did say I was shooting in the dark.
Good Luck

---

### Post by carolinason on 2007-06-07
In GNOME, KDE apps start very slowly because they have to load KDE libraries. There is no way around this unless I load KDE as the desktop.

Since xfce is gtk based, I would think that libraries would not be such an issue. I'll load xubuntu on my test machine and see.

orb has great points.

---

