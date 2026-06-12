---
title: "Software Manager Won't Remain Open"
date: 2016-12-23
forum: General Help
---

### Post by chunkydrew2 on 2016-12-23
My Software Manager in Ubuntu 16.04 will no longer open. I searched the forum and have not seen this discussed anywhere else. When I click on the icon to open, is loads to the screen for about 1 second, then closes immediately. I tried to update it using:
     [COLOR=#000000][FONT=&quot]sudo apt update && sudo apt full-upgrade
That completed without error messages, but the manager still won't open. Any ideas, anyone?[/FONT][/COLOR]

---

### Post by Bob_Dennis on 2016-12-26
I have the same problem.  When it first happened I got an error message that referred to some (unspecified) software that needed updating, so I ran the software-updater (lots of updates) and rebooted.  Now the software manager just dies with no message.  Ubuntu 16.04.1 LTS.  

I have noticed that in the last few months the software manager started to run much more slowly and sometimes would disappear temporarily if I entered a search term.  Don't know if that's connected in some way.  Note that the current problem is not temporary:  the software manager does not come back.

Help would be much appreciated.

---

### Post by wildmanne39 on 2016-12-26
@Bob_Dennis please start your own thread so you can get the help you need and the person that started this thread can get the help they need.

---

### Post by Bob_Dennis on 2016-12-26
Sorry, seemed like the same problem.

---

### Post by howefield on 2017-01-01
Try uninstalling the package and then reinstalling, seems to work for some.

```
sudo apt purge ubuntu-software
```
```
sudo apt install ubuntu-software
```

---

### Post by chunkydrew2 on 2017-01-01
***sudo apt-get update && apt-get upgrade*** worked for me. Thanks to those who replied.

---

