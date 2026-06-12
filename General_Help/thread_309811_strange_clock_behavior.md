---
title: "strange clock behavior"
date: 2006-11-30
forum: General Help
---

### Post by komaroveli on 2006-11-30
hi all,

every time i reboot computer my clock jumps 6 hours back (so if it's a 7pm in reality computer clock shows 1pm)
i have tryed with automatic time update on and off - same resolt. it still jumps back with 6 hours.
any thoughts?
thnx

ps i leave in europe so automatic update seerver i used was  europe.pool.ntp.org.
pps i leave in timezone GMT+1

---

### Post by Ramses de Norre on 2006-11-30
Check in /etc/default/rcS for the line ```
UTC=
``` and set it to no, this could be causing your problem if it is set to yes know.

---

### Post by malbery on 2006-12-22
I am getting a very similar problem. Essentially I can never trust the hours part of my clock as it keeps jumping around. Every time I connect to the internet (and/or restart I'm not sure) my clock hours jump around. I've tried both with an without ntp configured. This time I have a fresh 6.10 install.

My /etc/default/rcS file lists:
TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

---

### Post by wpshooter on 2006-12-22
How old are your computers ?

Have you considered the possibility that your CMOS battery is getting very weak  ???

---

### Post by malbery on 2006-12-23
Hmm. Good idea. I don't think that is it though. My laptop is modern and about 8 weeks old.

---

