---
title: "Several problems"
date: 2008-06-11
forum: General Help
---

### Post by scott20 on 2008-06-11
I am running Ubuntu 8.04 on a pentium 4 (3.06 GHz) With 1 GB of memory.  My problems are as follows:  Processor Usage shoots up to 100% (even when no applications are running; Update manager wont open (loading bar stops); Add/remove Applications wont open (loading bar stops); Synaptic Package Manager won't open (screen goes gray).

The only thing I have done recently was rip some CD's I own using Sound Juicer.  I don't know what to do and some input would be greatly appreciated.

---

### Post by Het Irv on 2008-06-11
1. All three of those programs use the same resources, and usally you cannot open all three at the same time. 

2. Are any other programs affected? Firefox? any of the Games?

---

### Post by scott20 on 2008-06-11
I'm using fireFox currently just fine and games seem to work too (I didn't check them all).  I haven't tried to open those programs at the same time.  They freeze and go gray and I have to close them using force quit.

---

### Post by Het Irv on 2008-06-11
Okay, sorry my confusion.
Try this then,
```
sudo apt-get update
```
it should go through and hit all of the mirrors

---

### Post by scott20 on 2008-06-11
I ran that code in Terminal and it went through the mirrors but at the end this was displayed. 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm not currently running anything except for Firefox.

---

### Post by drs305 on 2008-06-11
See if synaptic is still running in background with this command:
```
ps aux | grep synaptic
```
If you don't see synaptic, you can omit the **| grep synaptic** and see all running processes.

If it is listed, there will be a number (**PID)**near the left. Then:
```

sudo kill -9 **PID**

```

---

### Post by scott20 on 2008-06-11
I entered the first code and I got this:

scott     6681  0.0  1.2  33568 12920 ?        S    18:30   0:00 gksu /usr/sbin/synaptic
root      6682 81.2  2.5  46952 26496 ?        Rs   18:30  38:53 /usr/sbin/synaptic
scott     7418  0.0  0.0   1844   528 pts/0    R+   19:18   0:00 grep synaptic

Then I entered the second code and got this:

ERROR: garbage process ID "PID".
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.

What should I do?

---

### Post by drs305 on 2008-06-11
> **scott20 said:**
> I entered the first code and I got this:

scott     **6681**  0.0  1.2  33568 12920 ?        S    18:30   0:00 gksu /usr/sbin/synaptic
root      **6682** 81.2  2.5  46952 26496 ?        Rs   18:30  38:53 /usr/sbin/synaptic
scott     7418  0.0  0.0   1844   528 pts/0    R+   19:18   0:00 grep synaptic

Then I entered the second code and got this:

ERROR: garbage process ID "PID".
Usage:
  kill pid ...              Send SIGTERM to every process listed.
  kill signal pid ...       Send a signal to every process listed.
  kill -s signal pid ...    Send a signal to every process listed.
  kill -l                   List all signal names.
  kill -L                   List all signal names in a nice table.
  kill -l signal            Convert between signal numbers and names.

What should I do?

Run the code like this:
```
sudo kill -9 **6681**
sudo kill -9 **6682**

```

The third process is you looking for the other processes. ;-)

---

### Post by Het Irv on 2008-06-11
Did you change PID in drs305's command to one of the PID's (6681, 6682, or 7418)?

Dang, beat me to it! :lolflag:

---

### Post by scott20 on 2008-06-11
Ok that Brought my processor usage down to 50%.  This still higher than normal (0%-25%)

---

### Post by drs305 on 2008-06-11
> **scott20 said:**
> Ok that Brought my processor usage down to 50%.  This still higher than normal (0%-25%)

I thought we were working on a different problem (synaptic) ;-)

You can view what's using your memory, and a lot of other stuff, with:
```
top
```

---

### Post by scott20 on 2008-06-11
Top display shows PID 6296 (apt-check) is at %CPU 100.  Should I use that kill command for that as well?

---

### Post by drs305 on 2008-06-11
> **scott20 said:**
> Top display shows PID 6296 (apt-check) is at %CPU 100.  Should I use that kill command for that as well?

Yes, you can do that.

---

### Post by scott20 on 2008-06-11
Thank you for your help.

---

