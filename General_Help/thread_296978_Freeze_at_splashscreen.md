---
title: "Freeze at splashscreen"
date: 2006-11-10
forum: General Help
---

### Post by Möller on 2006-11-10
So, I've installed Ubuntu Edgy on my computer, started up Automatix, installed some codecs, and get an update-Automatix-messege. i also made these changes to enable extra-buttons on my mouse.

/etc/X11/xorg.conf
Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Buttons" "7"
        Option "ButtonMapping" "1 2 3 6 7"
        Option "ZAxisMapping" "4 5"
        Option "Resolution" "100"
  EndSection

After these changes, i cant start Ubuntu. The splashscreen shows up, but it freezes when the bar is filled and a blue and a green line appears over the screen. Look more like a graphic-problem to me, but I'm not sure. =/
Anyone knows how I can get my Ubuntu up and working again?

---

### Post by JonoMG on 2006-12-06
Hey Moller,

Just wanted to check how you'd gone with this? I have just installed *nix for the first time, so treat me nice and excuse any (really) stupid questions.

I had installed, grabbed the latest xorg install for the ATI drivers, attempted to set up my x800 and got the same response as you on attempting the reboot.

Look forward to hearing back.

Cheers,

Jono

---

