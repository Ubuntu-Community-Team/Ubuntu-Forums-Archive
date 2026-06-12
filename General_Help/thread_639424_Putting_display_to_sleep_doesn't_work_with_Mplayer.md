---
title: "Putting display to sleep doesn't work with Mplayer"
date: 2007-12-13
forum: General Help
---

### Post by csulok on 2007-12-13
Hello

I have a Fujitsu Siemens P17-2 LCD monitor that has energy saving functions, however in Ubuntu I have problems with it. Most of the nights I put myself to sleep with watching a few eps of a random tv show and expect the monitor to switch off after the videos are done playing.

For this, in the System > Preferences > Power Management I selected 'put display to sleep' after 10 minutes of idling.

When I start watching a movie in Mplayer, this Power Management feature clicks in after 10 minutes of watching a movie, which shouldn't happen, so I just move the mouse around, the monitor comes back. Then when a movie is finished it doesn't turn off anymore... showing the same image all night isn't good for an LCD monitor so this is quite a big problem.

I've done quite a few runs with a short idling time set and this happens everytime. It seems after stopping mplayer, the idling timer doesn't start or something.

My mplayer is custom built using:
```
#! /bin/bash
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer
cd mplayer/
./configure --enable-gui --enable-largefiles
sudo checkinstall --nodoc --default --pakdir=~/

```
I use the xv videooutput in it. My videocard uses the nvidia-glx-new package, oh and my WM is compiz-fusion set to 'extra effects'.

How could I fix this?
Thanks for all the help in advance ^^

---

### Post by shirilover on 2007-12-13
I ran into this problem as well and use thepython script from the following link.
[http://ubuntuforums.org/showthread.php?t=284804](http://ubuntuforums.org/showthread.php?t=284804)

---

### Post by csulok on 2007-12-13
> **shirilover said:**
> I ran into this problem as well and use thepython script from the following link.
[http://ubuntuforums.org/showthread.php?t=284804](http://ubuntuforums.org/showthread.php?t=284804)

How does this behave if I use gmplayer, which doesn't quit, as in the process doesn't stop after the movie is done playing?
How does this behave when my browser uses mplayerplug-in, so if I have a webpage open (usually there is) with a video object, there is an mplayer process running?

If I understand it correctly, both of these scenarios would mean the script would prohibit the display to be put to sleep while the video is running, and after that too, all night. So while it fixes that the monitor turns off during playback, it doesn't fix the all-nighter bug. Am I correct on this?

Thanks for your answer btw ^^

---

### Post by csulok on 2007-12-15
bump

---

### Post by csulok on 2008-01-06
shameless bump because this is going to kill my lcd panel :(

---

### Post by drdnl on 2008-01-17
I'll quit happily bump it up as well as I have a similar habit of watching ep's when I go to sleep (or falling asleep whilst) and own a 100 watt 24" lcd monitor.

The screen blanks (screensaver) but I'd like for it to go to sleep as well, save the planet a bit right? It's set to blank a minute after the (blank) screensaver kicks in, sometimes it works, usually it doesn't

Using stuff like "vbetool dpms off" you can force it to switch off, anyone know of a way to script it to run at a pre-determined time? Sometimes I use "sudo shutdown -hP 60" to as a way to blank my screen after 60 minutes but unfortunately that blanks alot more than just the screen...

---

### Post by csulok on 2008-01-17
that vbetool stuff sounds great, how do you recover your display from turned off monitor though?
shaking the mouse, pounding your head on the keyboard just doesn't cut it.. :)
typing vbetool dpms on blind in the terminal you left open last night may not work either.. :/

I'm thinking maybe doing a scheduled task in the terminal might work for your problem however:

```
sudo bash
at 00:00
vbetool dpms off
```

---

