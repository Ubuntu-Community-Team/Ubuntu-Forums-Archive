---
title: "wine edgy problems"
date: 2007-02-16
forum: General Help
---

### Post by vav on 2007-02-16
I was wondering if there is a way to make some wine programs run from an icon in the panel? I tried the 'application in terminal' option, but a terminal window pops up for less than half a second and then vanishes. The same command, when run in an open terminal window, runs well and starts the program in wine! How do I do this?

Another issue: please refer to figure, is that a program that I run in wine shows up with all text overlapping. I tried installing msttcorefonts etc, which didnt work. What could be the problem?

Thanks

---

### Post by Tobster on 2007-02-16
Just to clarify to start a application in Wine a left click and select 'open with Wine'
Linux Format Magazine in the UK done a trail with an Eliminator called Cross Over but this is closed source and cost around £30 which is the one that I am going to buy know I am new to this as well.

---

### Post by vav on 2007-02-16
Ok I found the solution to the first problem (creating a launcher)

Basically, you need a semi-windows style command. So in the launcher (no need to run in terminal),
wine "/home/xx/.wine/drive_c/Program\ Files/Prg/Prg.exe"  wont work, but
wine "z:\home\xx\.wine\drive_c\Program Files\Prg\Prg.exe" works great (wine calls my root partition the z drive, which is default for most users)

how lame is that? especially when the former works very well when typed in a terminal. :mad:

---

