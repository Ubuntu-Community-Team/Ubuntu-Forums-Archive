---
title: "GDM wrong resolution"
date: 2008-04-28
forum: General Help
---

### Post by guitarmaniac on 2008-04-28
OK I have had this problem for a long time now and it seems others do too.
Ubuntu and most other Linux distros seem to think that the optimal resolution for my computer is 1600 x 1200.
I change it to 1280 x 1024 which is fine when I'm logged in, but my GDM comes up at 1600 x 1200 which is barely readable.
It is only a minor annoyance as I have my computer set to log in automatically but its still a problem.
Anyone know how to fix this???

---

### Post by Nurionn on 2008-04-28
I don't now how to change that in Hardy. But in Gutsy I had to change it in the file:
*/etc/X11/xorg.conf*

An easy way to change it was the command (Change there only the resolution parameters and leave the rest as it is):
*sudo dpkg-reconfigure xserver-xorg*

---

### Post by rubicon on 2008-04-28
Unfortunately *sudo dpkg-reconfigure xserver-xorg* doesn't set the resolution. At least, for me. You have to manually edit xorg.conf like this (backup it before changing!):
```

Section "Screen"
[COLOR="Silver"]        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
[/COLOR]        SubSection "Display"
                **Modes   "800x600"**
        EndSubSection
EndSection

```

---

### Post by lenx on 2008-04-28
I have a similar problem since i got a new screen in waranty, my old one was broken. Somehow the firmware of that screen is wrong, my computer thinks it's default resolution is something else than the native 1280*1024.

So what happens when is start my computer is the same as you, as soon as the login screen appears the resolution is wrong! My solution is to start the computer with the power cable plugged out of my sceen. As soon as gdm started i can plug power in and resolution is fine (to what i set it in xorg.conf).

There is no other way to 'solve' it, i already spend many hours at this problem!

Now something interesting: yesterday i installed the kde desktop additional to gnome. When i used kdm instead of gdm to log into ubuntu, i don't have the resultion problem! so you could try that?
The only disadvantage is if you want to turn your system off, you have to log out and then turn off.

---

### Post by guitarmaniac on 2008-04-28
@rubicon

so where it says mode I'm assuming I just change the resolution to say 1280x1024 (you have 800x600)???

> Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        SubSection "Display"
                Modes   "800x600"
        EndSubSection
EndSection

@lenx
I was going to download Kubuntu 8.04 KDE 4 but I'm over my download limit :P
I may download it next month or hold out for openSUSE 11.


On a completely unrelated matter, whats with the lack of new KDE distros at the minute???
It's like everyone suddenly decided that GNOME was the better option all of a sudden (must have something to do with people not thinking KDE 4 isn't stable enough I guess).

---

