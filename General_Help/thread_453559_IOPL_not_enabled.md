---
title: "IOPL not enabled"
date: 2007-05-24
forum: General Help
---

### Post by gray380 on 2007-05-24
Hi there!

When I try to run some windoze programm under wine I get the following error:

"IOPL not enabled"

Any assistance?

brg,
Serhiy.

---

### Post by dpsguard on 2007-05-27
I am also running in the same issue. Basically I have tried to install Visio 2003, since I have not been able to find any open source package which can import / export files to Visio format (being properitary).

I have spent hours and hours to research finding this IOPL not enabled error issues but so far no resolution.

---

### Post by gray380 on 2007-06-26
seems it's ubuntu's problem (possibly library version), because the slackware has no such a problem.

---

### Post by benchMarc on 2007-07-01
Got exactly the same problem here. Running feisty and Wine, latest version: 0.9.40. Haven't found a sollution so far :(

---

### Post by yoshimitsu on 2007-07-23
I was fighting against the same problem with visio 2003 recently armed with wine 0.9.33 and kubuntu 7.04 (feisty).
Now I have wine-0.9.36 with same OS version and problem partialy defeated. I can run visio from my windows installation and can install visio under linux with wine (in that case you will get an error at the end of the installation, but that is ok, just rerun setup again and choose to reinstall).
The part of the problem left - visio is unable to open documents wich were created by the same version in windows. Opening files causes standart windows application fault. Do not know what to do with that now :( But, still, visio 2003 is able to launch.

---

### Post by yoshimitsu on 2007-07-23
A little update for the situation. Drawing can be created/saved/opened while using linux visio installation.
Problems with opening files created by another visio installation are at place.

---

### Post by eschuch on 2007-08-22
Hello All

You must set wineprefix
export WINEPREFIX="~/.wine"

---

### Post by eschuch on 2007-08-22
Hello All

Correction

You must set wineprefix

$export WINEPREFIX="home/erico/.wine"

Or where your 'drive_c' , 'system.reg' and 'user.reg' files are.

---

### Post by Showpan on 2007-11-09
How, more details please!

---

### Post by eschuch on 2007-11-15
You must have de WINEPREFIX set to run nicelly wine.
2 ways to do it:
Edit /etc/enviroment and add at the end of file the:
> 
WINEPREFIX="/home/~/.wine"

Or set it itch time you run wine with:
> 
WINEPREFIX="/home/~/.wine" wine winfile.exe

Note that *winfile.exe* is the file that you are running on wine.

Hope helps.

[eschuch.blogspot.com]("http://eschuch.blogspot.com")

---

### Post by ajmorris on 2007-11-24
hey eschuch,
Dont know about other people, but that didnt work for me. I still get the IOPL not enabled error. (I tried adding it to the file, and with it in-front of my wine command.)

---

### Post by dembel91 on 2008-05-05
Look at here guys!
It was a problem for me, untill I've installed [winetricks]("http://wiki.winehq.org/winetricks").
Then, in winetricks I install "dcom98". In winecfg, in libraries tab I've choose rpcrt4.dll - build.
So, Microsoft Excell Viewer works fine. Wine 0.9.58.

---

