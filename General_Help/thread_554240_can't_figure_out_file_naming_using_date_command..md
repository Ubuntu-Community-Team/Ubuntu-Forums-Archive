---
title: "can't figure out file naming using date command."
date: 2007-09-18
forum: General Help
---

### Post by ridetheteapot on 2007-09-18
Hey, i've been trying to set up cron to record a few npr shows from the radio station where i used to live.
For the most part i know how to do if through crontab and mplayer. But when mplayer creates the file i want to name it by date.

this is the portion im having trouble getting to work:

mplayer -dumpfile wnycmorning_date +%b%d.mp3

  Using this the file will be named "wnycmorning_date". obviously not exactly what i was hoping for. What i want is "wnycmorning_Sep17.mp3".

i know there is a way to do this because i have used uname with apt-get to get the right linux-headers package; but alas i can't remember how.

---

### Post by jamvegan on 2007-09-18
I'm not sure if this works in cron, but in a shell script, wnycmorning_`date +%b%d`.mp3 would do the trick.  (Note that those are "back ticks", generally next to the 1 on the keyboard, *not* single quotes.)

---

### Post by cmnorton on 2007-09-18
I am not sending this from a linux system, so I cannot test it first:

DATE_STR=`date +%b%d`
mplayer -dumpfile wnycmorning_${DATE_STR}.mp3

---

### Post by ridetheteapot on 2007-09-24
hey thanks a bunch jamvegan. i had been trying to use the ' ' regular single quotes.

---

