---
title: "Problem with executables"
date: 2008-05-31
forum: General Help
---

### Post by DocHolliday2006 on 2008-05-31
Hi. I sometimes have problems with not being able to get .exe or .run files to work. Right now I just installed the open source freespace 2 game.I got it from here: [http://www.hard-light.net/forums/index.php/topic,42854.0.html](http://www.hard-light.net/forums/index.php/topic,42854.0.html)

I opened the installer using java.



The executable for the game in the directory the installer created is called freespace2.exe. I click on it and it doesn't know how to open it. What program do I have to select so it can open it? Java doesn't work.

Any advice on .exe files welcome, because double clicking does not work, for this program or for others. 

Thanks.

---

### Post by quelx on 2008-05-31
the **.exe** files are windows executable only but may work in **wine** ([https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)).

The .run files probably need to be made executable or run with **sh**.

Right click the **.run** > **Properties** and check the permissions.  Make sure the **x** (e**x**ecutable) box is checked and try running it again.

You can also open a terminal windows and ```
chmod +x mybinary.run
./mybinary.run
```

or```
sh mybinary.run
```

---

