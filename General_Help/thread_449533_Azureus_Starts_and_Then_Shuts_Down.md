---
title: "Azureus Starts and Then Shuts Down"
date: 2007-05-20
forum: General Help
---

### Post by jmoody83 on 2007-05-20
I'm not sure what happened, it was downloading about 5 torrents when it just shut down. I restarted it and it goes through it's start-up then when the main window shows it shuts right back down. I've restarted my computer, uninstalled it, and reinstalled it. Still does the same thing every time. It's very frustrating. Anyone have any ideas?

---

### Post by misfitpierce on 2007-05-20
Perhaps uninstall java completely and reinstall java runtime completely... Maybe a java problem as azereus is a java based program... I use Transmission myself :p

---

### Post by jmoody83 on 2007-05-20
I go to System->Preferences-> and under there I see Sun Java 5.0 (and plug-in) and Sun Java 6.0 (and plug-in) which do I uninstall?

---

### Post by nikhilk on 2007-05-20
Probably before reinstalling JRE you might want to delete the older preferences and see if that works. I am not sure but the preferences are probably stored in the directory ~/.azureus. WARNING: All your settings will be lost after running the command ```
rm -rf ~/.azureus
```

---

### Post by cisforcojo on 2007-05-20
Agreed. DON'T remove Java yet. This happens to me all the time (unfortunately). 
Delete /home/yourname/.azureus like the previous poster said.

You'll lose all your downloads and progress though. The files will still be there as downloaded but your downloads will all be removed from azureus. I'm not sure if it's possible to resume or not. (I'd bet almost anything it is possible but I don't know how to do it.)

---

### Post by ryukent on 2007-05-20
The problem is a bug in 2.5.0.0. If you goto:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

And download the latest version, then open the archive and replace the /usr/share/java/Azureus2.jar with the one in the archive, it should solve the problem.

Worked for me. Now using 2.5.0.4 This way you don't need to delete your .azureus directory either.

---

### Post by techno-mole on 2007-05-23
ryukent wrote - 

The problem is a bug in 2.5.0.0. If you goto:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

And download the latest version, then open the archive and replace the /usr/share/java/Azureus2.jar with the one in the archive, it should solve the problem.

Worked for me. Now using 2.5.0.4 This way you don't need to delete your .azureus directory either.

ok so ive been having the same problem with azureus, in that it shuts down a few seconds after starting up, ive tried using - rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*
this works ok for a while, but it will stillshut down after a few minutes.
so ive downloaded the 2.5.0.4 version and i can run it fom the home folder, but if i want to replace the azureus2.jar file as you mentioned above i cant because i dont have the right permissions, so how do i change the permissions ? i thought id ask here rather than starting a new thread, any help will be appreciated.
cheers

---

### Post by xopher_mc on 2007-05-24
open terminal and type this in. 

sudo cp Azureus2.jar /usr/share/java/

using sudo gives you root permission temporarily. Your gonna use this a lot. ;)

---

