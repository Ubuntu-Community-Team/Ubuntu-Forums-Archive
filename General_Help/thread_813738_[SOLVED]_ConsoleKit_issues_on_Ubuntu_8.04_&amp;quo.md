---
title: "[SOLVED] ConsoleKit issues on Ubuntu 8.04 &amp;quot;Hardy&amp;quot;"
date: 2008-05-31
forum: General Help
---

### Post by dustigroove on 2008-05-31
I have just completed a fresh CLI install of 8.04 on my desktop machine and set'er up with X.org/Openbox as my environment. While in the process of fleshing out the system  tools that I wanted on there I ran into a deep bog with PolicyKit and ConsoleKit. Apparently if you don't go with the default install (standard, full-bore, ubuntu-desktop system) then it leaves these two new-with-Hardy packages a bit buggered.

So here's the general gist:

I installed the gnome-system-tools package to give me some decent graphical tools to handle user and group management, as well as date, time, etc. However after install I found that Hardy's new-fangled PolicyKit and ConsoleKit stuff isn't fully cooked on my system and that the users-admin and other GNOME system tools now use an unlock button to be able to do your magic instead of running as su. Spiffy! Well, in theory anyway... in practice um, not-so-much. When running any of the the tools all the buttons and boxes are grayed out, including unlock. So I can look at the tools, but do absolutely nothing with them, awesome. So then, on to the Googling and all the manual file cajoling needed to get these tools to a usable state. Finally after much hunting and some riveting reading of bug reports pertaining to PK and CK, I came across the ck-launch-session and ck-list-session commands. Running ck-list-session returns info on the current ConsoleKit session, and when I ran it I got... zilch. Aha! So I then ran ck-launch-session and... viola, session info was now a go and I could launch users-admin and actually make changes.

However not all was as it seemed in Wonderland. Here is my issue; I cannot for the life of me find any information as to the proper way ck-launch-session is supposed to be called up. From playing a bit I can pretty much deduct when it needs to be run, after dbus is up at boot and before running X. Also, it seems that the way I got it running isn't 100% correct as it doesn't require me to unlock any of the tools. Doesn't exactly give me that warm fuzzy feeling having it run like that.

So here's my request/challenge... can any of you kind folk with Hardy installs that are humming along smooth as silk see how your ConsoleKit's session is launched on your system? Also for a bonus if someone could post their default PolicyKit.conf and hal.conf files, well that would just be peachy-keen.

Thanks in advance!

Cheers,

---

### Post by dustigroove on 2008-05-31
Any takers? Really would appreciate a hand here!

:)

---

### Post by dustigroove on 2008-08-26
:ks bump :ks

---

### Post by infinito on 2008-10-08
Did you managed to fix this? If affirmative, how?

---

### Post by dustigroove on 2008-10-08
> **infinito said:**
> Did you managed to fix this? If affirmative, how?

Unfortunately, no. I have since upgraded my machine and just have a standard install of Ubuntu, so there was no need to look into the issue further, sorry!

---

### Post by infinito on 2008-10-09
> **dustigroove said:**
> Unfortunately, no. I have since upgraded my machine and just have a standard install of Ubuntu, so there was no need to look into the issue further, sorry!

Well, yesterday i finally got it working. I'm using Openbox, and login using a text console, and then typing "startx".

So to init Openbox with consolekit support, I have this on my ".xinitrc" file:
```
exec ck-launch-session dbus-launch --exit-with-session openbox-session
```

This way, you get a openbox session, with dbus and consolekit enabled.

Hope it helps!

---

