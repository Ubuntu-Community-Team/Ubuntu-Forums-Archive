---
title: "flashplayer 8?"
date: 2006-07-06
forum: General Help
---

### Post by anubix on 2006-07-06
so not all the time, but alot of times since i upgraded to newbuntu (whatever the latest is out i upgraded to friday) i've been getting alot of errors where flash videos should be "you need flashplayer 8 to view this video", and i'm given a link to macromedia, where for linux the latest version is flashplayer 7
anyone else running into this?
or better yet know how to rectify it?

pz

---

### Post by aysiu on 2006-07-06
Adobe/Macromedia doesn't make a Flash 8 player for Linux. They are planning to make a Flash 9 version, though.

---

### Post by Zlatan on 2006-07-06
you can install some flash-player using package manager

[QUOTE=anubix]so not all the time, but alot of times since i upgraded to newbuntu (whatever the latest is out i upgraded to friday) i've been getting alot of errors where flash videos should be "you need flashplayer 8 to view this video", and i'm given a link to macromedia, where for linux the latest version is flashplayer 7
anyone else running into this?
or better yet know how to rectify it?

pz[/QUOTE]

---

### Post by aysiu on 2006-07-06
[QUOTE=Zlatan]you can install some flash-player using package manager[/QUOTE]
Yes, Flash player 7.

---

### Post by anubix on 2006-07-06
so the general concensus is that i'm assed out 'till some corporate fat-cat at macromedia decides he'd rather spend money devoloping a new flash player for linux instead of his puerta-rican mistress in palm beach?

---

### Post by aysiu on 2006-07-06
You can install Firefox for Windows in Ubuntu using Wine. Then, visit a Flash site using that Firefox and install the plugin for Flash 8. ```
sudo aptitude update
sudo aptitude install wine
cd
wget -c ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.4/win32/en-US/Firefox%20Setup%201.5.0.4.exe
mkdir firefox
wine "Firefox Setup 1.5.0.4.exe"
``` Install it to /home/anubix/firefox in the setup wizard. Finish the rest of the wizard, but do not launch Firefox at the end. ```
mv ~/firefox ~/.firefox
wine ~/.firefox/firefox.exe
```

---

### Post by anubix on 2006-07-06
so, ur saying to go back to windows?
after i've gone through all this trouble to kick 'em through the uprights?

---

### Post by _simon_ on 2006-07-06
No, he's not saying that. He's saying to use WINE to install the windows version of firefox and then download the flash plugin that way.

---

### Post by anubix on 2006-07-06
and that'll allow me to view flash 8 stuff using my linux firefox?
OR just while i'm using the wined firefox
and if it works in the linux firefox, can i then delete the wine firefox?

---

### Post by DoktorSeven on 2006-07-06
It allows you to install Flash 8 in the Firefox running under Wine; it won't let you run Flash 8 in the Linux version of Firefox.  Keep both versions, and if you need to view a Flash 8 site, use the Wine version.

---

### Post by zba78 on 2006-07-06
you can use the portable firefox from [http://portableapps.com/apps/internet/browsers/portable_firefox](http://portableapps.com/apps/internet/browsers/portable_firefox)

download the Zip Download, extract it then run that firefox through wine. Got to a flash website (like [http://www.hitentertainment.com/portal/flash/player.asp](http://www.hitentertainment.com/portal/flash/player.asp)) and firefox will download and install flash 8

---

### Post by WADemosthenes on 2006-07-10
Is wined firefox, being run through another program, slower than running firefox normal?  Anyway, sounds like a good idea, I'm going to try it when I get some more free time :D

---

### Post by aysiu on 2006-07-10
Wine runs at native speeds because it is not an emulator:
[http://www.winehq.com/site/myths](http://www.winehq.com/site/myths)

---

### Post by puelocesar on 2006-07-10
> **WADemosthenes said:**
> Is wined firefox, being run through another program, slower than running firefox normal?  Anyway, sounds like a good idea, I'm going to try it when I get some more free time :D
I'm using wined firefox to play some games in neopets.com

And, I must say that the performance is the same.

---

