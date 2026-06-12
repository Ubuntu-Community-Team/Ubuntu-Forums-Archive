---
title: "Ubuntu 12.04_4 NO SOUND"
date: 2014-04-07
forum: General Help
---

### Post by craig1980 on 2014-04-07
[FONT=arial]Hi there[/FONT][FONT=arial]
[/FONT]
[FONT=arial]I just installed ubuntu 12.04_4 LTS 64bit on my Fujitsu; 
I had to install also Postgres&PostGIS on it and I installed the last version of Postgres and PostGIS; in order to install PostGIS I built it on my PC and I had to instal the following modules:[/FONT]
[FONT=arial]
[LIST]
[*]GEOS
[*]Proj.4
[*]GDAL
[*]LibXML2
[*]JSON-C
[/LIST]
From when I installed the listed modules (above all the last 2) I have no sound on my laptop; when I try to activate pulseaudio I get this error:
[/FONT]
[FONT=arial]"[/FONT]
[FONT=arial]pulseaudio -D
pulseaudio: symbol lookup error: /usr/lib/x86_64-linux-gnu/libpulse.so.0: undefined symbol: json_tokener_parse
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]"[/FONT]
[FONT=arial]It seems that the json-c lib and lixml lib caused some problems; in my old 32bit machine this didn't happen; any suggestion about how i can solve this issue?[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thank you

Angelo[/FONT]

---

### Post by craig1980 on 2014-04-08
Any suggestion? Should I uninstall and install the OS once again? I hope it's not the only solution....
Any tips is really apreciated

Angelo

---

### Post by craig1980 on 2014-06-10
Does anybody have a suggestion? I'm not able in solving this issue...and I can't format my laptop

Angelo

---

