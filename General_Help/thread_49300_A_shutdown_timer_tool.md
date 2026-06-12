---
title: "A shutdown timer tool"
date: 2005-07-15
forum: General Help
---

### Post by Moebius on 2005-07-15
Hi there, is there any small tool that could enable be to specify a certain shutdown time (countdown style) for Ubuntu?

It would be usefull for me, setting a designated time for my PC to shutdown, specially when going to bed and leaving the PC doing some downloads.


Cheers

---

### Post by smoon on 2005-07-15
[QUOTE=Moebius]Hi there, is there any small tool that could enable be to specify a certain shutdown time (countdown style) for Ubuntu?

It would be usefull for me, setting a designated time for my PC to shutdown, specially when going to bed and leaving the PC doing some downloads.


Cheers[/QUOTE]

Fire up a terminal of your choice and use `shutdown'. For example ```
shutdown -h 12:00
``` will shut your computer down at 12 o clock. ```
shutdown -h +60
``` will do it an hour after you issue the command. See ```
man 8 shutdown
``` for more details ;-)

---

### Post by Moebius on 2005-07-15
[QUOTE=smoon]Fire up a terminal of your choice and use `shutdown'. For example ```
shutdown -h 12:00
``` will shut your computer down at 12 o clock. ```
shutdown -h +60
``` will do it an hour after you issue the command. See ```
man 8 shutdown
``` for more details ;-)[/QUOTE]
 Ah, great. Thanks for the heads up.

Cheers

;)

---

### Post by maxdevis on 2006-01-28
and what if i forgot the time and i want to know what time i had set it to shutdown?

---

### Post by ryu kun on 2006-11-22
> **maxdevis said:**
> and what if i forgot the time and i want to know what time i had set it to shutdown?

As long as the terminal open, output tells... if not, you can cancel it by: ```
sudo shutdown -c
```

---

### Post by ponkarthik on 2006-11-22
HI
 If you are using KDE use Kshutdown which has lots of options. U can shutdown at specified time or a certain time from now. You can also shutdown other programs at any specified time.

I use it regulaly without any problem.

Karthik

---

### Post by creaturex on 2006-11-23
If you want to set for a certain time repeatedly, you could always add it to your crontab (man crontab to learn how). Same for any process or script you want to run at specified times.

---

