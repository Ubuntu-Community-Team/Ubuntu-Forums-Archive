---
title: "Could not get lock /var/lib/dpkg/lock"
date: 2007-07-12
forum: General Help
---

### Post by quatro4 on 2007-07-12
Hello,

When I want to do something with sudo apt-get , this message shows up.

tolga@tolga-linux:~$ sudo apt-get install xchm (For example)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Please help me . Thank you..

---

### Post by smartbei on 2007-07-12
You probably either have synaptic open, or have another terminal window open running apt-get, or have the update manager running... chck and see if any of those are running.

---

### Post by McNils on 2007-07-12
Only one program can hold the lock. Make sure that you are not running aptitude, synaptic or adept. Close the program and rerun and it should work.

Try this commant in a terminal.
```
ps -e | grep -e apt -e adept | grep -v grep
```

---

### Post by quatro4 on 2007-07-12
Thanks for helping me. I will try these solutions.

---

