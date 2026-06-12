---
title: "envy24control killed it"
date: 2007-03-04
forum: General Help
---

### Post by bb4r on 2007-03-04
Greetings all; I've got a lot of good info simply lurking here, but now I need some help with either 1) rescuing this system or 2) getting advice on what to copy to my other drive to make life easier if I have to reinstall (e.g., myth/mysql database, etc.)

I am using 6.10 as mainly a PVR as combined front/backend mythtv box.  Out of the box, only the analog outs on my m-audio delta ap 2496 worked, but I got both s/pdif and analog working at the same time.  I could switch between inputs on my amp and get sound though amaroK and mythtv (both live and recorded TV).

But I noticed that the sound quality was better from analog than from spdif.  Saw a post about envy24control and how it is more like the delta control panel that comes with mac/windows drivers for m-audio.

So I installed it. (sudo apt-get install alsa-tools-gui).
Big mistake.:mad: 

Ran it once and...
1) s/pdif out immediately stopped.
I didn't change anything, just quit as soon as spdif quit.

2) sound for mythtv recordings is high-pitched.  Like everyone's sucking on helium.  (Sound on these recordings was fine with both analog and spdif before installing alsa-tools-gui).

Removed alsa-tools-gui but the problem remained.  Ran alsamixer and noticed that "multi track internal clock" that was previously set to 48000 was now set to "IEC958" (or perhaps IEC958 1, can't remember).  All else was the same.

reboot and enter problem 3 (the big one):  

X starts, but hangs prior to login with the default rusty orange background screen.  I'm using autologin, but I 'm pretty sure it's hanging before logging in.

CNTRL ALT F1, login as root (password enabled on this machine) and looked at /var/log/Xorg.0.log and no errors of note.  

/etc/init.d/gdm start

replies starting gdm [OK] but nothing happens and

startx

tells me a session is already running so I 

rm /tmp/.X0-lock
startx

and I get the same story but this time it hangs on loading the wallpaper.  I can start gdm from rescue mode but still hangs at login.

Any suggestions are *greatly* appreciated.

---

