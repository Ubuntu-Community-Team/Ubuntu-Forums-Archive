---
title: "[SOLVED] Missing controls on windows"
date: 2007-11-28
forum: General Help
---

### Post by dpwilson on 2007-11-28
Not sure what to call them, but I am missing the "maximize", "minimize" and "x" close window buttons from the top of any window I open.  Any ideas how to get them back?

---

### Post by PeterJS on 2007-11-28
Well that depends... What window manager are you using?

---

### Post by dpwilson on 2007-11-28
Not sure.  I am completely new to ubuntu.  I had them a few days ago, but just noticed that they are gone now.  How do I tell what window manager I am using?

---

### Post by PeterJS on 2007-11-28
I'm going to assume that you're running the gnome desktop (which is the default), so you're either using Emerald (if you have advanced effects enabled), or Metacity (if you do not).

---

### Post by dpwilson on 2007-11-28
I havent changed anything since installing gutsy other than as you mentioned, I changed the visual effects to "extra".

---

### Post by PeterJS on 2007-11-28
That would be metacity then, of which I don't know much about, sorry :(

---

### Post by dpwilson on 2007-11-29
Rebooted and everything returned to normal.  Guess I should have tried that first.  Thanks.

---

### Post by Drate on 2007-11-30
Oh bummer, I am having the same problem, scept I startd with a minimal install, and am using metacity, but rebooting does nothing.  I was hoping somebody would gnow what i need to install or what file I need to configure to fix this.  Is this an xorg.conf problem?

I've tried dpkg-reconfigure xserver-xorg but to no avail.

---

### Post by Drate on 2007-12-02
For all those concerned, reinstalled metacity (rebooted to see if it fixed it), nope, ran "metacity --replace" (rebooted to see if it fixed it), yep. Maybe I didn't need the first reboot, but who cares? That process seems to have done the trick permanent.

---

### Post by forestpixie on 2007-12-02
with an nvidia card I added the 2 red lines

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 MX 440 with AGP8X"
    BusID          "PCI:1:0:0"
    Screen          0
    [COLOR="Red"]Option         "AddARGBVisuals"     "True"
    Option         "AddARGBGLXVisuals"  "True"[/COLOR]

which worked, I'm using compiz-fusion and emerald - had to add the same to my second screen in xorg to get it to work there as well.

---

### Post by nisarg on 2008-03-22
EDIT:
Infact it didnt. It brought the coInfact it didnt. It ntrols back, however it did switch visual effects to NONE again.

------

great - that worked.. thanks
just curious what was the problem though? and what did the metacity --replace do ?

> **Drate said:**
> For all those concerned, reinstalled metacity (rebooted to see if it fixed it), nope, ran "metacity --replace" (rebooted to see if it fixed it), yep. Maybe I didn't need the first reboot, but who cares? That process seems to have done the trick permanent.

---

