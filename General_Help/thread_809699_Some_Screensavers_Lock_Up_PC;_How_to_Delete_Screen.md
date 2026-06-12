---
title: "Some Screensavers Lock Up PC; How to Delete Screensavers?"
date: 2008-05-27
forum: General Help
---

### Post by Teasdale on 2008-05-27
I found this [old thread]("http://ubuntuforums.org/showthread.php?t=207123&highlight=lattice") where someone said they had solved the problem of certain screensavers locking up their computer by deleting those screensavers:

"I had to go through and delete four of the screensavers because they completely locked up my (actually my lady friend's) system by just selecting them: Flipscreen3D, AntSpotlight, Lattice and Matrixview."

I'd like to delete them, but I can't figure out how. I found the folder they're in usr\lib\xscreensaver but it denies me permission when I try to move them to trash.

So far I've verified (by accident) that even previewing Lattice locks up both my computer and my son's. We're both running Gutsy.

---

### Post by jb1972 on 2008-05-27
Mine is doing similar where every screensaver scrambles the screen then hangs my pc (ubuntu hardy 8.04). Even previewing screensavers does it. I'm also getting it with some games too. My pc is old but i wouldn't expect it to bugger up like it is. Dell optiplex gx50, standard onboard graphics.

---

### Post by Teasdale on 2008-05-28
It seems to be a fairly common problem, something about 3D screensavers, and it probably has to do with video card problems.

So, have you figured out a way to delete those screensavers?

---

### Post by chadjohnson on 2008-06-22
I have found that the following GL screensavers lock up my system consistently (or make my system VERY slow):
[LIST]
[*]xrayswarm
[*]imsmap
[*]interaggregate
[*]whirlwindwarp
[*]substrate
[*]braid
[*]vermiculate
[*]zoom
[/LIST]

I'm not complaining; I know this is free software. Just making note. To remove these screensavers, you can do the following:

```

sudo rm -rf `locate -i screensavername`

```

Be careful removing the Zoom screensaver, however, as there are other files on your system that have "zoom" in their names. You might just run locate -i screensavername before adding on the rm -rf part.

Also, webcollage pulls random pr0n from the web about 50% of the time...probably not good if your family members or a girlfriend walk in your room.

Note that I am using an nVidia card (8800 GTS w/ 320 MB RAM) and a 6000+ X2 processor wtih 2GB RAM. And the system is, on average, < 35C.

---

