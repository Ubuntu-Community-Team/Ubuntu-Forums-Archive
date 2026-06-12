---
title: "Login"
date: 2006-12-02
forum: General Help
---

### Post by koulanji on 2006-12-02
After trying to install my sound drivers on a fresh kernel, my gdm was removed in the middle of removing the drivers, and when I restarted, I was unable to login. I got this  error:

"Your session lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem"

The details for the ~/.xsession-errors file
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/x11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x /var/lib/gdm/: 0,Xservers -h "" -l ":0" "axisaudio"

/etc/gdm/Xsession: Beginning session setup

(skipping a few, as I now realize that these are processes apart of the login)

exec: 4: gnome session not found

I have tried logging in by means of failsafe, but I get the same error. Any thoughts? I'd love to get back to my terminal and desktop and fix this horrid mess

---

### Post by blitze on 2006-12-07
Not sure if this will help as I am suffering the same problem myself as you when I was trying to install a 32bit lib for Quake 4.

What I am going to try is a re-installatioin of gnome desktop and see if that helps.

I am a little frustrated after how long it took for me to learn how to get my snd card working but C'est la vie as they say in France. ](*,) 

Good luck

---

### Post by Adramelech on 2006-12-07
Its a common problem but i didnt recall what i answered :P

I supposed you read a HOWTO to install your sound drivers, well in that HOWTO is the solution, just scroll down and heres a gnome-something command to get all working again (i guess you read the same howto :)

---

### Post by koulanji on 2006-12-07
> **blitze said:**
> Not sure if this will help as I am suffering the same problem myself as you when I was trying to install a 32bit lib for Quake 4.

What I am going to try is a re-installatioin of gnome desktop and see if that helps.

I am a little frustrated after how long it took for me to learn how to get my snd card working but C'est la vie as they say in France. ](*,) 

Good luck


Try this [guide]("http://www.psychocats.net/ubuntu/nox") man

---

### Post by blitze on 2006-12-07
I did read the Howto for my specific card from the Alsa site.  It is annoying though that I have to download the drivers from Alsa direct and then have to build them because the packages from Ubuntu are 
1. Older
2. Not including what was needed to get the thing working, namely the alsa firmware specific to my card.

Once compiled and placed in the firmware folder for Edgy with a reboot, every thing worked but again there were issues with multi output and configuring the card in general.

What I am trying to imply is that sound is an important part of computing nowdays and Linux distros should try do work a little more on making getting sound happening at installation with minimal fuss.  Moreso than wobbly windows and some pretty effects on your desktop.

Sound like video output in Linux though craps on Windows, once working (subjective to my hearing and eyes) :)

---

