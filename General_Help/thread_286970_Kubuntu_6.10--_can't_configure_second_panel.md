---
title: "Kubuntu 6.10-- can't configure second panel"
date: 2006-10-28
forum: General Help
---

### Post by Dawnshadow on 2006-10-28
I installed Kubuntu 6.10 on my laptop last night, after using 6.06 on my desktop machine for a few months. (Today I get to set up the wireless card. Wish me luck.) However, I've come across an issue. While using Ubuntu with Gnome, I got hooked on the two-panel setup. (I just like Kubuntu's eye candy.) So, when I went over to KDE, I made a second normal panel on the top of the screen and did a Gnomeish panel arrangement.

However, in 6.10, once I added the second panel, right-clicked on it, and hit 'configure panel,' it brought up the options screen for the main panel. There was no dropdown box ("settings for...") to choose which panel to configure. All changes were only applied to the main panel. I added an external taskbar panel, and the same thing happened-- I was unable to change the lize, and could only change its position by dragging it across the screen.

Is this a bug? A "feature?" My laptop being quirky? Thanks.

---

### Post by mafitzpatrick on 2006-10-28
I can confirm that I have the same problem... and I was wanting to do exactly the same thing! But that unfortunately doesn't help.

Would be nice if kubuntu came default with a ubuntu-like arrangement, no?

---

### Post by mafitzpatrick on 2006-10-28
Ok, I've discovered that if you add another Panel then go to configure panel, you can choose which panel you are choosing settings for (drop down list at the top).  Let me know if that works for you - and indeed if it is there (I hadn't spotted it until I started digging around in config files and changing stuff!)

---

### Post by mafitzpatrick on 2006-10-28
Quick update...  For some reason the option to change which panel you are editing is only available if you first open ~/.kde/share/config/kickerrc (e.g. with Kate) and then save it again.  I've tested this on a second desktop and it's reproducible.

With that available it is possible to configure the desktop as you like.

I am going to make available a "template" of the Ubuntu desktop under KDE, which a test version is [available here](http://www.mutube.com/downloads/ubuntu-panels-KDE.tar.gz) (or [here](http://www.mutube.com/downloads/ubuntu-panels-KDE.tar.gz?coral-no-serve)).  Download and extract the files into ~/.kde/share/config/ and let me know how you get on!

I think I'll post a bug about that menu-after-save weirdness.

---

### Post by Jucato on 2006-11-03
I can confirm this bug. I don't think it's a Kubuntu-only bug, though, since I don't have any Kubuntu default settings. 

Btw, you just need to restart kicker to make the drop-down list reappear

```
dcop kicker kicker restart
```

---

### Post by BioN on 2006-11-10
> **Jucato said:**
> 
Btw, you just need to restart kicker to make the drop-down list reappear

```
dcop kicker kicker restart
```

Ah i have been searching for the last half an hour on how to fix this problem cheers mate that fixed it up.

---

