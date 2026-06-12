---
title: "Problem: random slow-downs of 7.04"
date: 2007-09-30
forum: General Help
---

### Post by vpervouchine on 2007-09-30
Hi everyone,

The problem started with upgrade to Ubuntu 7.04. First, the booting process is often really slow - far slower than it used to be before the upgrade. Second, the desktop sometimes just slows down randomly, once or twice a day, to the point of becoming unusable: the mouse cursor moves slowly, cannot start any application, terminal window becomes useless, etc. If left for a while (10 minutes or so) the problem may or may not disappear.

I searched this and other forums to find descriptions of similar problems, checked /var/log/messages but didn't find anything suspicious there. Also ran memtest and fsck with no results (everything seems OK). I have no idea what to look into next. Any suggestions?

---

### Post by scrooge_74 on 2007-10-01
Post the specs of your system maybe someone will know.

I had some issues to so I decided to go back down and not use 7.04

---

### Post by vpervouchine on 2007-10-08
It looks like the problem was with the swap. It was not mounting because of [this bug]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/90526"). Now after I fixed it everything works as normal.

---

