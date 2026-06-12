---
title: "Unexpected shutdown of system"
date: 2015-03-08
forum: General Help
---

### Post by chazzyfresh33 on 2015-03-08
I'm currently using Mint 17.1 Cinnamon on an Asus UX31E Ultrabook, but this issue has also persisted in installations of Ubuntu 14.04 and Xubuntu 14.04 so I'm trying to cover as much ground as I can.
Certain tasks seem to shut down my system when on battery, mainly playing video (streaming or local) at full screen. It's not as bad as it was, until a trip to a local repair shop the mere act of opening a browser would crash it, but it seems that video will cause the crash then. 
Here's what I know on the problem:
-Opening a browser at less than 70 % battery does not trigger a crash  anymore, unless I attempt to stream something full screen (Netflix,  YouTube, Facebook videos, etc).
-Chrome seems to be more stable than Chromium in this respect
-Resolution does not seem to be a factor
-Problem occurs regardless of whether hardware acceleration is turned on or off
-Just  for kicks, I logged into one session in software rendering mode. The  crash occured there while streaming YouTube as well (which was painful, I  might add)
-The crash also occured while watching a local copy of a  1080p video with VLC, although it took much longer to do so than a  streaming video generally would
-Apport continues to not create crash logs for this event.
-Syslog   does not seem to have record of the most recent one either (in fact,  it has nothing logged for the two hours prior to my noting that VLC  caused the crash as well).
-I did contact the previous owner to attempt to get  a more complete machine history and found that he had no issues of this  nature while Windows was installed, and that he in fact used the  machine for gaming.
-Google Earth also caused a crash once.
Anyone have any idea what my issue could be and how to fix it?

---

### Post by dino99 on 2015-03-08
Looks like the chipsets temperature is going a bit too high; and so the system is protecting itself by shutdown process.
First idea indeed is to check to fan(s): do they work at all ? You can follow the speed and temperature(s) with some plugin(s)
Secondly be sure that the system can breath (not too dusty) and get some fresh air (dont set your hardware onto something already hot, and/orthings avoiding hot air going out and fresh air coming into it)

---

### Post by dragonfly41 on 2015-03-08
> unless I attempt to stream something full screen (Netflix,  YouTube, Facebook videos, etc).

Another item on checklist might be flash plugin.

Do the same symptoms show across different browsers?

Can you run say firefox with add-ons disabled (look at Firefox > Help > Troublshooting)

---

### Post by chazzyfresh33 on 2015-03-08
I'm guessing probably fans then, as I rarely hear them and disabling addons has never helped

---

### Post by tgalati4 on 2015-03-08
Previous owner?  So with an uncertain history, one must assume that this machine as seen extensive gaming under Windows, which means the graphics chip has gotten quite toasty.  The thermal stresses cause the chip to warp and delaminate from the motherboard.  The kernel doesn't know how to handle this situation so you get either a kernel panic (keyboard lights flashing) or a graphics freeze and a black screen.  

Search the web for reviews, perhaps you are not the only one with an Asus Ultrabook that has graphics problems.

---

