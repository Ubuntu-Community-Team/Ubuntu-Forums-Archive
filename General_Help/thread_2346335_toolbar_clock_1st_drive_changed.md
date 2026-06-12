---
title: "toolbar clock 1st drive changed"
date: 2016-12-13
forum: General Help
---

### Post by oneleded on 2016-12-13
i have XP on 1st drive, Lubuntu on 2nd drive.. every time i use 2nd drive, the toolbar clock, bottom right on XP drive displays incorrect time, when i use it. is this normal? the clock on Lubuntu is on military time[24hrs]. i cant see that being a problem, though it might be. when i used the dvd-r with Lubuntu, it did the same thing, to 1st drive.[2nd drive was not in use at that time]. i am upgrading Lubuntu 14.04, to 16.10. any ideals are appreciated.  //Ed

---

### Post by irongolem0982 on 2016-12-13
try: ```
[COLOR=#111111][FONT=Consolas]# timedatectl set-local-rtc 1[/FONT][/COLOR]
```


Good Luck!

---

### Post by oneleded on 2016-12-27
> **irongolem0982 said:**
> try: ```
[COLOR=#111111][FONT=Consolas]# timedatectl set-local-rtc 1[/FONT][/COLOR]
```


Good Luck!

is that command a root command? the terminal does not say, that its invalid, yet i still got the same problem. i'm not logged on as a superuser, i dont know how yet. lubuntu is on 24hr time, windows is on 12hr time. i cant seem to change lubuntu time to 12hr.

---

### Post by oneleded on 2017-03-11
i found out that in my profile, im am in western europe, instead of ky.  i have tried to set that more than once.. only should i get out of the hollar.  //Ed
 i wish to delete what i just posted as it serves no purpose, plus this forum has nothing to do worth the time difference, between 1st, wondows hard drive, and the 2nd, linux hard drive time problems. i am sorry that i even posted this.  //Ed

---

### Post by oneleded on 2017-03-28
i went to 16.10.. it was not LTS. so i reformatted back to 14.04 and tried to update to 16.04LTS. it was a failure. however, the time difference, between 1st an 2nd hard drive is not there. 1st HD being windows, 2nd l HD being lubuntu. 14.04 had some problems sort of corruption when i tried to update to 16.04.  //Ed

---

