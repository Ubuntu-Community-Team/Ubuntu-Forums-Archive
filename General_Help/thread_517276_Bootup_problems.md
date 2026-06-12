---
title: "Bootup problems"
date: 2007-08-04
forum: General Help
---

### Post by wiberg on 2007-08-04
Hi, i recently got a new computer and I have a problem with it. On bootup, 2 out of 3 times the bootup process will freeze when the ubuntu logo appears and the status bar is at about 1/4. Everytime, on the third attempt, Ubuntu boots perfectly fine.
As I just recently switched to Ubuntu I can't figure out the reason for this on my own :| But I'll give you some information about my system (dmesg is pretty long so i put it elsewhere for you to take a look at it):
[dmesg]("http://paste.ubuntu-nl.org/32486/")
[my System]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00462576&lc=en&cc=us&dlc=en&product=501194&lang=en") (its a "HP Media Center m7170.ch Desktop PC")
uname -a:
Linux jojohp 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

I am happy to provide any additional information!
Greetings,

wiberg

---

### Post by TBerben on 2007-08-04
dmesg is utterly useless in this case, because before you have access to its output, the system must have booted... And because the system booted succesfully, no errors will show up :p (not to put you down, usually dmesg output is quite useful, just not in this case, at least, I think it is ;)) Can you switch to vt1 when you're booting? (Ctrl-Alt-F1), that virtual terminal contains the output from the current boot process, if you can get a peek at the output when the process hangs you might be able to spot an error

---

### Post by wiberg on 2007-08-06
Alright, it seems to be this:

soft lockup detected in cpu0#
soft lockup detected in cpu1#

why does this happen randomly? and more importantly, how can i fix that?

---

