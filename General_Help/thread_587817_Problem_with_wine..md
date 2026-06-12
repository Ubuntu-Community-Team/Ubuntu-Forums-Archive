---
title: "Problem with wine."
date: 2007-10-23
forum: General Help
---

### Post by viergeame on 2007-10-23
I installed a program (PokerStars) through wine, and for awhile it was working great other than being a little slow.  Today I opened it and was played for awhile and had no problems.  Later on when I tried to open the program to play I clicked the icon and nothing happened.  I waited several minutes just in case it was lagging then I checked the list of running processes.  It was on the list, but the window never showed up.  I tried restarting, since that seems to magically fix so many things, but no dice.  I'm not sure what to think of this since the program was working fine just a few hours ago.

---

### Post by kripkenstein on 2007-10-23
Perhaps try to run it from the command line. That is, do something like
```

wine /path.to.program/program.exe

```
in a terminal. That way, if it crashes or has an error, you might see the output. Then post it here, perhaps it will make sense to somebody.

---

### Post by sdil on 2007-10-23
i think, that is not the big problem ... maybe you just the X Window of the game you play. You need to ' end process ' the game using System Monitor.

---

### Post by viergeame on 2007-10-23
I'm having a problem opening it from a terminal because one of the folders above it has a space in the name and it just stops reading it at the space.  I don't know what to do about this...

nikki@ubuntu:~$ wine /home/nikki/.wine/drive_c/Program Files/Pokerstars.exe
wine: cannot find '/home/nikki/.wine/drive_c/Program'


And regarding sdil's suggestion, efore I asked on here I tried restarting to fix it and that didn't work, so killing the process doesn't seem to do anything.

---

### Post by kripkenstein on 2007-10-23
> **viergeame said:**
> I'm having a problem opening it from a terminal because one of the folders above it has a space in the name and it just stops reading it at the space.  I don't know what to do about this...

nikki@ubuntu:~$ wine /home/nikki/.wine/drive_c/Program Files/Pokerstars.exe
wine: cannot find '/home/nikki/.wine/drive_c/Program'

To deal with the space, do a reverse slash before the space:
```

wine /home/nikki/.wine/drive_c/Program\ Files/Pokerstars.exe

```
Or, write the line up to "Program" (before the space), and press tab. It should then autocomplete "\ Files" and you can continue to type (but this won't work if there is another folder with a similar name).

---

### Post by zaphod777 on 2007-10-23
try wine "/home/nikki/.wine/drive_c/Program Files/Pokerstars.exe"

---

### Post by viergeame on 2007-10-23
I've tried using the reverse slash and the quotes around the file name and I still am getting the message saying it can't be found.  I've checked to make sure I was spelling everything right and had all the correct capitalization.

Also, I did look on the system monitor again to see if it was running from when I first tried it after my last restart.  I tried to end the process and instead of ending it said it's a zombie.  I'm not sure what that means.

Maybe my computer is trying to tell me I shouldn't play any more poker. :(

---

### Post by zaphod777 on 2007-10-23
can you cd "/home/nikki/.wine/drive_c/Program Files/" 
and then 
ls 
does it show the file? you need the quotes on the whole path if there is a space. Linux needs the comand here option like the xp power toy.

---

### Post by songshu on 2007-10-23
if it can't be found are you sure it is there?

---

### Post by zaphod777 on 2007-10-23
are you sure we are here?

---

### Post by viergeame on 2007-10-23
I just tried and I can cd to /home/nikki/.wine/drive_c/Program Files/ and it works as long as I don't use the quotes around it.

---

### Post by zaphod777 on 2007-10-23
so from that  directory can you launce the program by typing wine and then the program name

---

### Post by viergeame on 2007-10-23
Awesome, it finally worked!  Thank you all very much.  You have no idea how happy I am to have that program working again.

---

