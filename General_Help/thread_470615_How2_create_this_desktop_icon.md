---
title: "How2 create this desktop icon"
date: 2007-06-11
forum: General Help
---

### Post by Sockerdrickan on 2007-06-11
WINEDEBUG=-all wine "/home/robin/Spel/cod/CoDSP.exe"

And make it run in a terminal?

---

### Post by BennBuntu on 2007-06-11
Just working from the default launcher from a wine app I've got

env WINEPREFIX="/home/fonzo/.wine" wine "C:\Steam\steam.exe"

then created a new launcher (right click on Desktop"
Chose type, "application in terminal"
and used

WINEPREFIX="/home/fonzo/.wine" WINEDEBUG='-all'  wine "C:\steam\steam.exe"

Give that a shot.

---

### Post by BennBuntu on 2007-06-11
yours might just need the quotes ='-all', not really sure

---

### Post by Sockerdrickan on 2007-06-11
Same problem :(:(

An error was encountered while trying to create the childprocess for this terminal

---

### Post by Sockerdrickan on 2007-06-11
Using WINEPREFIX="/home/robin/Spel/cod/" winedebug='-all' wine "codsp.exe"

Just wine "/home/robin/Spel/cod/CoDSP.exe" works, the problem is that it can't handle the WINEDEBUG=-all (only 1 "command")

---

### Post by BennBuntu on 2007-06-12
mine gives that error wihout the "env" bit in front, 
don't know what it does, try.

env WINEDEBUG='-all' wine /home/robin/Spel/cod/CoDSP.exe

works for me

---

### Post by Sockerdrickan on 2007-07-15
If anyone is looking at this, I found a bullet proof way, SHell script

save this as cod.sh

WINEDEBUG=-all wine "/home/robin/Spel/cod/CoDSP.exe"

and set permissions to "blablabla i want to run this as a program"

done :]

---

