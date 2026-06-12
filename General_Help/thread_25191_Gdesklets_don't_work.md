---
title: "Gdesklets don't work"
date: 2005-04-09
forum: General Help
---

### Post by artinla on 2005-04-09
I installed gdesklets and opened the desklet manager.  I selected the ones I wanted and then File/Run Selected Desklet.  Nothing happens.  

I have never used gdesklets before, so it is probably something simple.

---

### Post by dataw0lf on 2005-04-09
Are you sure the actual 'gdesklets' app is running? Start it (by typing nohup gdesklets & at the prompt) if it isn't.

---

### Post by artinla on 2005-04-09
art@flatulus:~$ clear
art@flatulus:~$ nohup gdesklets
nohup: appending output to `nohup.out'
art@flatulus:~$ ps -aux | grep gdesk
art      23075 95.3 34.9 192888 180544 ?       R    06:54 118:58 python /usr/lib /gdesklets/gdesklets-daemon
art       1233  0.2  3.4  25636 17892 ?        S    08:51   0:01 python /usr/lib /gdesklets/gdesklets-shell
art       2359  0.0  0.1   2876   724 pts/0    S+   08:59   0:00 grep gdesk
art@flatulus:~$


Still nothing happens when I select the clock for instance and try to start it.

any other ideas?

---

### Post by Xian on 2005-04-09
Maybe it's just the sensor. Try the [_GoodWeather_](http://gdesklets.gnomedesktop.org/categories.php?func=gd_show_app&gd_app_id=204) desklet. I know it works in Hoary.

---

### Post by artinla on 2005-04-09
That one doesn't work either.. it was one of the ones I wanted to add to my desktop to begin with.

They all look like they load, but I get nothing on my desktop.

---

### Post by UbuWu on 2005-04-10
You are not the only one having problems with gdesklets

[http://www.ubuntuforums.org/showthread.php?t=22071](http://www.ubuntuforums.org/showthread.php?t=22071)

---

### Post by ciascuno on 2005-04-16
Not sure if this'll help but it worked for me when nothing would appear on my desktop - you could try installing python-gnome2-extras from the Universe with Synaptic.  Saying that, I gave up on the Hoary package and had compiled gDesklets from source before I tried that but it might work without all that extra work!

Hope you get it sorted

c

---

### Post by MOPAULY on 2005-05-29
The only way I could get gdesklets to work was to downoad it from the main site.  It took awhile as it would fail based on missing dependencies, but I was finally able to get it working.

---

### Post by joele on 2005-05-29
[QUOTE=artinla]That one doesn't work either.. it was one of the ones I wanted to add to my desktop to begin with.

They all look like they load, but I get nothing on my desktop.[/QUOTE]

I had the exact same problem, I gave up on it to be honest I can't be bothered spending all that time on it.....

I may consider downloading the source and compiling myself though, a pain though as the package is there!!!

---

### Post by Psquared on 2005-05-29
[QUOTE=artinla]I installed gdesklets and opened the desklet manager.  I selected the ones I wanted and then File/Run Selected Desklet.  Nothing happens.  

I have never used gdesklets before, so it is probably something simple.[/QUOTE]

What version of gDesklets do you have and where did you get it? If you got it from Synaptic or apt-get did you install the gdesklets-data file too? If so, uninstall it (the data file) and download your desklets from [www.gdesklets.gnomedesktop.org](www.gdesklets.gnomedesktop.org). I have version 0.34 (0.35 is out but you have to compile it) and most of the desklets work for me. A few fail because they were written with a different code (something called psi) but you will get an error message.

I have Goodweather working great. I also use NewsGrabber (RSS feeds) and an inbox monitor for email.

---

