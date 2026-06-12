---
title: "Lubuntu digital clock changes BIOS to UTC time"
date: 2015-08-01
forum: General Help
---

### Post by steve169 on 2015-08-01
I run Lubuntu Mini 15.04.

When I boot my live Lubuntu USB stick, all goes well, but when I log out, Lubuntu changes the BIOS time to UTC. 

After Lubuntu makes the change, the time is displayed incorrectly in Windows, an annoyance.

I faintly remember when installing Lubuntu that it asked whether I should put the digital clock on UTC or local time. I don't remember which I chose.

Could that be the problem? If so, how can I correct it in Lubuntu?

---

### Post by VMC on 2015-08-01
What does "/etc/default/rcS" say? Somewhere around line 21.
It should say "UTC=no"

---

### Post by steve169 on 2015-08-02
You hit the bull's-eye, VMC. The reS file had "UTC=yes."

But when I open it in the text editor and try to change it to "no," I get an error message: "Can't open file to write."

In Windows I would go to Properties and turn off the file's read-only setting. But I can't find anything similar in Lubuntu.

---

### Post by NoWayWin8 on 2015-08-02
You need to use administator:
```
gksu gedit /etc/default/rcS
```
(you might need to install gksu first if not installed already)

---

### Post by kerry_s on 2015-08-02
> **NoWayWin8 said:**
> You need to use administator:
```
gksu gedit /etc/default/rcS
```
(you might need to install gksu first if not installed already)

lubuntu uses leafpad:

```
gksudo leafpad /etc/default/rcS
```

not sure if leafpad has made the update to pkexec, but you could try:

```
pkexec leafpad /etc/default/rcS
```


i know mousepad in xubuntu can use the new pkexec policy, but i've never tried leafpad.

---

### Post by steve169 on 2015-08-02
Got it. Many thanks to all. We newbies would perish without the generosity of you pros.

---

### Post by Yellow Pasque on 2015-08-02
Please mark the thread solved.

Note that you can also modify Windows to use UTC instead of altering (L)ubuntu: [https://wiki.archlinux.org/index.php/Time#UTC_in_Windows](https://wiki.archlinux.org/index.php/Time#UTC_in_Windows)

---

