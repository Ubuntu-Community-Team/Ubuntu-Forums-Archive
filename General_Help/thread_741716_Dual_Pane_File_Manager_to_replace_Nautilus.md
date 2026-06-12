---
title: "Dual Pane File Manager to replace Nautilus"
date: 2008-04-01
forum: General Help
---

### Post by Kiri on 2008-04-01
I'm looking for a dual pane file manager for ubuntu to replace nautilus. But Nautilus seems pretty integrated into ubuntu. Is it possible to replace it without messing stuff up and causing problems?

And does anyone have any favorite dual pane file managers?
On windows I used to really like Xplorer2... Looking for something like that for linux
thanks!

---

### Post by Whiffle on 2008-04-01
Konqueror does dual panes and happens to be my favorite.

---

### Post by Kiri on 2008-04-01
I was thinking about that one. But does it integrate into gnome ok?

Edit: Did you mean Konquerer or Krusader?
I thought Konquerer was not dual-pane...

---

### Post by ShodanjoDM on 2008-04-01
[emelfm2]("http://emelfm2.net/") : [http://en.wikipedia.org/wiki/EmelFM2](http://en.wikipedia.org/wiki/EmelFM2)
[Gnome-Commander]("http://www.nongnu.org/gcmd/") : [http://en.wikipedia.org/wiki/GNOME_Commander](http://en.wikipedia.org/wiki/GNOME_Commander)

emelfm (not emelfm2) and gnome-commander are available in the repository. Don't know why the emelfm2 isn't available there yet

---

### Post by Whiffle on 2008-04-01
> **Kiri said:**
> I was thinking about that one. But does it integrate into gnome ok?

Edit: Did you mean Konquerer or Krusader?
I thought Konquerer was not dual-pane...

Never had any desire to integrate it into gnome, so I can't help you there, but it defintily does dual pane...

---

### Post by Kiri on 2008-04-01
Thanks for the suggestions. 
I tried emelfm2, looked good, but had a few quirks with the interface I found annoying. 
gnome-commander didnt really do it for me.

And I just installed Konqueror and it looks good in web mode, but whenever I try to change it to file manager mode it crashes, so I really cant tell what it is like :(

Is there a command to start it in file manager mode? The installer only added it as a web browser app in the menu

---

### Post by Whiffle on 2008-04-02
Konqueror uses profiles to manage this.  If you run in terminals:
konqueror --profiles 

it will list all the ones it has.  THen you can launch it with a profile by doing
konqueror --profile midnightcommander

(which is the one i screenshotted above)

---

### Post by Kiri on 2008-04-02
Got it working thanks. Looks good

---

