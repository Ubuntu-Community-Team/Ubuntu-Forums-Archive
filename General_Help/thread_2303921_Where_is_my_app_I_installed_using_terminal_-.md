---
title: "Where is my app I installed using terminal - ?"
date: 2015-11-22
forum: General Help
---

### Post by michael-piziak on 2015-11-22
[SIZE=2][COLOR=#333333][FONT=Verdana]sudo add-apt-repository ppa:bearoso/ppa[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]sudo apt-get update[/FONT][/COLOR]
[COLOR=#333333][FONT=Verdana]sudo apt-get install snes9x-gtk[/FONT][/COLOR]

  

  [/SIZE][COLOR=#333333][FONT=Verdana][SIZE=3][SIZE=2]This came from the website:  [http://www.upubuntu.com/2012/09/a-list-of-best-game-console-emulators.html](http://www.upubuntu.com/2012/09/a-list-of-best-game-console-emulators.html)

I installed Snes9x using the above terminal code - it worked for me many times in the past.  I even did it twice in terminal.
I can't find Snes9x on the dock or in the dash home.  Please direct me to where it is at on my computer.
[/SIZE]
[SIZE=2]Michael[/SIZE]
[/SIZE][/FONT][/COLOR]

---

### Post by Hodevah on 2015-11-22
The program may or may not be in **/opt**. This directory normally would hold user installed programs. But not all the time. 
Other locations it may or may not be are in **/usr/bin**/
If you like, you can use the **find **command. In terminal go **man find **for usage.

---

### Post by CantankRus on 2015-11-22
Are you sure you installed it?
Terminal is saying the ppa doesn't exist....
```
**[COLOR="#006400"]glen@Trusty:~$[/COLOR] sudo add-apt-repository ppa:bearoso/ppa**
Cannot add PPA: 'ppa:bearoso/ppa'.
Please check that the PPA name or format is correct.
```

To list files installed by a package....
```
dpkg-query -L [COLOR="#808080"]<package>[/COLOR]
```

---

### Post by michael-piziak on 2015-11-22
> **CantankRus said:**
> Are you sure you installed it?
Terminal is saying the ppa doesn't exist....
```
**[COLOR=#006400]glen@Trusty:~$[/COLOR] sudo add-apt-repository ppa:bearoso/ppa**
Cannot add PPA: 'ppa:bearoso/ppa'.
Please check that the PPA name or format is correct.
```

To list files installed by a package....
```
dpkg-query -L [COLOR=#808080]<package>[/COLOR]
```

You are right, I have not installed it.
Well shucks.  Where can I get Snes9x ?   It's my favorite emulator, even though it has not been worked on in a long time!

Michael

---

