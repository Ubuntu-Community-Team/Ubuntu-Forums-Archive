---
title: "Mic heard and controlled by Ubuntu but not by applications?"
date: 2008-05-31
forum: General Help
---

### Post by jasontu on 2008-05-31
I have an odd problem that I just cannot solve no matter what I try:

I have a mic in the front jack of my PC.  

I can mute/unmute/volume control the thing from the Volume Control within Ubuntu.

I cannot, however get it to be heard or picked up by either the Linux or Wine version of TeamSpeak or the Wine version of Vent with either another wine program running or not.

Any suggestions?

Thank you!

---

### Post by ellgor on 2008-05-31
Hi,

Try this, open a terminal and type alsamixer, a new window will appear with a pretty basic column chart representing the individual appliances on your system (if this window doesn't appear you will need to install alsamixer-gui).
Using the arrow keys move along the columns until Mic is highlighted, the up and down keys are volume control, the little box at the base of the column should be green indicating its on, if not press M-m to enable it, hopefully this should get the mic working for you.

Regards, Ellgor.

---

### Post by jasontu on 2008-05-31
Thank you for the tip but that apparently wasn't the issue.  The mic was turned on and the volume was turned up.  I can hear the input coming out the speakers.

However if I go into say, Sound Recorder, I click on the Record from Input and the menu is blank.  Also if I hit record and start talking... nothing gets recorded.  I am using the onboard audio on an Intel Chipset motherboard.  I believe the chip set is....GA-945GCM-S2C

Thanks

---

