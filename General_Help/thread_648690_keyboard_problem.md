---
title: "keyboard problem"
date: 2007-12-23
forum: General Help
---

### Post by mrcold on 2007-12-23
the buttons on my keyboard have to be held down for about one second for them to respond.

The problem is not there on the login screen

I am using 7.10 and have disabled compiz

I have not recently changed or installed anything

sorry for being so terse...      this takes forever


help?

---

### Post by mrcold on 2007-12-24
i hate to be impatient, but this problem needs to be fixed ASAP

any ideas?

---

### Post by tgalati4 on 2007-12-24
In a terminal, look at the results of:

>top  (control-c to quit)

Looks like something is taking 100% of your cpu cycles.  Write down the process ID number (PID#) and then:

>sudo kill -9 PID#

---

### Post by mrcold on 2007-12-24
thanks for the tip, but the top of the list was rtorrent, and it was only using 1.3%

i killed it anyway and the problem remains

---

### Post by mrcold on 2007-12-24
solved... as it turns out my sister was playing a prank on me

there is a setting in keyboard preferences called "slow keys"

thanks for the help

---

