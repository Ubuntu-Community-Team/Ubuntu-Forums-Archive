---
title: "[SOLVED] Applications Menu not launching program"
date: 2008-06-26
forum: General Help
---

### Post by pofigster on 2008-06-26
I just installed Neverwinter Nights - the installation went fine and the game runs great.  The problem shows up when I added a "NWN" link in the Games section of the Applications menu.  I set the path to the game correctly (I've done this before with Rainslick Precipice of Darkness) but it won't run from the menu.

If in the terminal I navigate to the installation directory and type ./nwn - it runs.  If I browse in nautilus to the install directory and double click on the file it'll run.  It's only from the applications menu that it doesn't work.  Other things do work from the menu when I install them in the same way.

Any ideas on what the trouble could be?

---

### Post by mempman on 2008-06-26
the problem has to do with the path of your file that you want to run not being in your path.  This is prolly the cause since you are able to launch in elseways.

You have 2 solutions:
add the repective dir to your path
OR
create a script, and place script in your path, such as:

```

cd /usr/dir/dir/program-dir
./program

```

---

### Post by VMC on 2008-06-26
That's almost like mine. I have the following example:
> cd /home/vmc/games
wine CHESS.EXE

Then I create a launcher on my desktop pointing to that shell script

---

### Post by pofigster on 2008-06-27
How do I change my path?  Like I said, I've done things like this before with Enemy Territory, Unreal Tournament 2003 and Rain Slick Precipice of Darkness...

I checked again in the Application menu, the correct file to run is in the path - it looks exactly the same as the menu item I have for RSPoD...

If there's a "path" file I'm supposed to change to include this - please let me know where it is.  Thanks.

Command for RSPoD in the menu:
```
/home/mark/rainslickep1/RainSlickEp1
```

Command for NWN1 in the menu:
```
/home/mark/NWN1/nwn
```

---

