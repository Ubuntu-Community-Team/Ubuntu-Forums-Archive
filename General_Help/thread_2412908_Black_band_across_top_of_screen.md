---
title: "Black band across top of screen"
date: 2019-02-18
forum: General Help
---

### Post by melcomub on 2019-02-18
I too have this problem but the solution offered doesn't work for me.
I have Lubuntu 18.10 on a Lenovo V110 notebook, dual booting with Win10. On starting Lubuntu, the desktop appears, filling the screen as expected, then several milliseconds later, it shrinks vertically to leave a black bar at the top approx 1cm. wide. Perhaps an unhelpful driver or service being loaded near the completion of the startup? 
Booting 18.10 from a live USB displays perfectly, so the issue seems confined to the installation. LXQt setting>Monitor setting>Resolution shows the correct resolution (1366x768) for both live and installed versions (even though the installed version is shrunk). Windows 10 also reports 1366x768 and fills the screen.
The black bar remains even if I change the resolution (via LXQt settings) to any of the other settings offered.
This is a new installation - I'm setting up the machine for someone else - and the problem has been there from the start.
The mouse pointer and Right button are active on the black bar, but icons dragged onto it disappear as if going behind a curtain.
I've explored the wallpaper options ("Stretch to fill screen, Zoom to fill screen" etc with no fix.
Any clues, please?
Many thanks in anticipation.

---

### Post by QIII on 2019-02-18
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2406744").

Adding your issue to a thread already marked solved is not likely to attract attention.  Furthermore, insinuating yourself into the thread of another user is a recipe for confusion for you, the OP and anyone trying to help.

Please start your own threads.  While your symptoms may appear to be very similar, the solution may be entirely different.

---

### Post by melcomub on 2019-02-18
Thanks - apols for the misunderstanding.

---

### Post by melcomub on 2019-02-25
Solved! It was actually a "Panel" which had somehow been made during installation,  or perhaps I'd inadvertently created it. Deleting it fixed the issue.

---

