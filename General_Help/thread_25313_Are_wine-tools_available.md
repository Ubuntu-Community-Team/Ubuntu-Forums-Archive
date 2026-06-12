---
title: "Are wine-tools available?"
date: 2005-04-09
forum: General Help
---

### Post by Robert S on 2005-04-09
I recently successfully managed to install wine-tools on a gentoo machine.  Makes installation of windows programs much easier on Linux.  Is this available in Ubuntu/Kubuntu?  I couldn't find it in the Universe.

---

### Post by humanity_to_others on 2005-04-09
Try these repositories:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by az on 2005-04-09
I have not had success with Wine from Universe

This worked for Warty a few months ago, but I am having trouble with the current version:
[http://www.winehq.com/site/download](http://www.winehq.com/site/download)

---

### Post by Robert S on 2005-04-10
I'd have to agree that wine/winetools in Hoary is a bit bodgy(*,).  I got a lot of error messages and crashes, and I couldn't get ie6 to run.  I got a message somewhere that winetools hadn't been tested with this version of wine.  Maybe its too bleeding-edge.

Not wanting to brag about other distros, but I got this combination working almost perfectly with Gentoo recently and managed to install Office 2000 for the first time ever. ]

---

### Post by mulino on 2005-04-11
[QUOTE=humanity_to_others]Try these repositories:
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/QUOTE]

Well, this worked perfectly for me! Thanks a lot!
mulino

---

### Post by Deusiah on 2005-04-13
Wine and Winetools in Hoary are hopeless. I'm not sure what's gone on there. I just disabled the Hoary repo so synaptic would install wine from the winhq repo instead and it works great for me :)

Make sure that you lock the winehq version of wine so you don't upgrade it by mistake.

---

### Post by az on 2005-04-13
Wine is under constant development.  I would not be suprised if in a week, the packages stopped working again for a few days.

Like using Sid.

---

### Post by Deusiah on 2005-04-13
OK when I said it works for me I should have said it works better for me as Photoshop loads and quits for no apparent reason yet Imageready works fine.

I think this is a Hoary issue since I'm using this exact same version of Wine on a another PC running Warty and it has no problems with Photoshop.

---

