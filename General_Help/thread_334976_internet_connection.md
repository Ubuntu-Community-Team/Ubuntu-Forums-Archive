---
title: "internet connection"
date: 2007-01-09
forum: General Help
---

### Post by terb on 2007-01-09
i have installed ubuntu edgy eft on my computer along with winxp. i tried to find linux drivers for my installed winmodem but linmodems did not have them for my modem. in this forum i read of a few of the members were using Diamond Supra serial external modems and i bought one. well-- it works very well with xp but ubuntu does not recognize it. i know very little about computers so please bear with me -- those of you who have a diamond modem do  you have both xp and linux on your computer? if so do you have drivers for both xp and linux ?  does anyone have some suggestions as to what i can do?? i have pages of terminal commands and i am pretty sure i have my internet connections fo ubuntu right. 
one other question-- i downloaded Gnome-ppp on windows and put it on a cd and installed it on ubuntu but the device manage said it could not open it--  thank you for any help

---

### Post by reclusivemonkey on 2007-01-10
> **terb said:**
> in this forum i read of a few of the members were using Diamond Supra serial external modems and i bought one. well-- it works very well with xp but ubuntu does not recognize it.

An external modem is a "standalone" device, and Ubuntu won't "recognise" it like other device internally in your PC. Its more like a broadband router. Assuming you have your modem connected to your serial port, you can use

```

minicom -c on

```

To check to see the modem is actually working. Now I did get several computers with Linux installed working with external modems and I had no problems at all, but this was many years ago and it was with Slackware not Ubuntu. There is a very detailed instruction here;

[http://www.linux.org/docs/ldp/howto/Modem-HOWTO.html](http://www.linux.org/docs/ldp/howto/Modem-HOWTO.html)

There is a debian specific HOWTO here;
[http://www.aboutdebian.com/modems.htm](http://www.aboutdebian.com/modems.htm)

Can you actually hear the modem dialing?

---

### Post by Johnsie on 2007-01-10
Get broadband :-)

---

### Post by terb on 2007-01-10
thank you -reclusive monkey and johnsie- 
no the modem just sets there not a peep
johnsie i hardly use the computer that much

---

### Post by reclusivemonkey on 2007-01-10
> **terb said:**
> thank you -reclusive monkey and johnsie- 
no the modem just sets there not a peep
johnsie i hardly use the computer that much

Which serial port do you have it plugged into?

---

