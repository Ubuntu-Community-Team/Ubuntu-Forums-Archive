---
title: "How to autostart Snort"
date: 2008-03-27
forum: General Help
---

### Post by cwhitmore on 2008-03-27
I've got snort working, but not sure how to get it to autostart when the server boots. There is already a snort daemon in /etc/init.d, but I'd like it to run with these settings:
snort -c /etc/snort/snort.conf -i eth0 -D

Do I need to take out the existing snort and replace it with script like snort.sh and the settings above?

---

### Post by -grubby on 2008-03-27
I'm guessing that's what you would do, but if it doesn't work I would suggest somehow adding it to a startup script of some kind..

---

### Post by xautofzx on 2008-05-29
> **cwhitmore said:**
> I've got snort working, but not sure how to get it to autostart when the server boots. There is already a snort daemon in /etc/init.d, but I'd like it to run with these settings:
snort -c /etc/snort/snort.conf -i eth0 -D

Do I need to take out the existing snort and replace it with script like snort.sh and the settings above?


sudo vi /etc/rc.local

/usr/local/bin/snort -c /etc/snort/snort.conf -i eth0 -g root -D

---

