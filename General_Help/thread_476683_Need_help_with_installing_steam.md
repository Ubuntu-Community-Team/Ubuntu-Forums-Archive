---
title: "Need help with installing steam"
date: 2007-06-17
forum: General Help
---

### Post by ChopperX on 2007-06-17
Ok i know you can run steam and im a gamer so steam is kinda crucial :D

Can someone guide me through the whole process? Ive tried it and doesnt seem to run.

---

### Post by dfreer on 2007-06-17
there are plenty of threads here that cover the process, could you tell us what you tried and what didn't work?

---

### Post by ChopperX on 2007-06-17
Well i tired to install wine and i dont think it installed.  But i would just start from scratch.

---

### Post by ChopperX on 2007-06-17
Ok i got steam working but i cant actually change my texture details. When i do it closes.

---

### Post by ChopperX on 2007-06-18
anyone gonna help?

---

### Post by Crafty Kisses on 2007-06-18
> **ChopperX said:**
> anyone gonna help?

It's probably crashing you may need to install your Video Card drivers.

---

### Post by ChopperX on 2007-06-18
My DirectX hardware is at level 6 instead of the normal 9

---

### Post by KushMaster on 2007-09-10
I have wine 9.44 and i installed steam.exe from steampowered.com , my problem is when it is updating, it reaches 26% and it stops, and a window pops up and says. " steam is already running, You may only run one copy of steam at a time" Then i click ok and wine closes. Can anyone please tell me how to resolve this problem ?

---

### Post by dfreer on 2007-09-11
The 26-28% crash is a bug that's been around for quite awhile, and I don't remember seeing it in the 9.3X and 9.4X versions. It may have to do with you using an older version of the Steam Client installer (the latest version is an .msi file).

This may also help, although I have never used it myself:
```
wine SteamTmp.exe SelfUpdate "C:\Program Files\Steam\Steam.exe" 14
```
Changing the "nice" level of wine/steam may help also:
```
nice -n 19 wine Steam.exe
```

BTW, all of this info is from winehq.org AppDB. Next time, when dealing with wine issues, try that site first and then report here if you still have problems :D

---

