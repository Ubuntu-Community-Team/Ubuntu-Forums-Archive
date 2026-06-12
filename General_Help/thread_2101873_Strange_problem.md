---
title: "Strange problem"
date: 2013-01-05
forum: General Help
---

### Post by steve97usa on 2013-01-05
Hi all
I'm having a very very strange problem and I need some help to figure it out.
Let's start with the basic data. Ubuntu 10.04 LTS updated.

uname -a
Linux Oliver3 2.6.32-45-generic #101-Ubuntu SMP Mon Dec 3 15:41:13 UTC 2012 i686 GNU/Linux

It updated also libraries and utilities.
Before the last update everything was working just fine.
After the last update (yesterday) everything still works but one machine in my network is not reachable anymore from this machine.
My network has all assigned IP manually.
The updated machine with Ubuntu 10.04 LTS, let's call it Alpha, has the IP of 192.168.1.80 and the unreachable one, let's call it Omega, the IP 192.168.1.60.
All the other machines in my network can access Omega withou problems, as Alpha  was able to do before the update.

Is not a network problem, Alpha  is connected to the network, can see and access all the machines BUT not Omega.
Ping, ssh, vnc, http, nothing.
I also connected Alpha to the same router of other machines.
Still nothing, so it must be something about Alpha and is not physical since I can see and connect with other machines and to internet from Alpha.
Only Omega become invisible to Alpha !!

I suspect that the last update mess up something in the network configuration of Alpha but I was unable to find something strange.

Any suggestions about how to find and fix this problem ?

Many many thanks !!
  STeve

---

### Post by ajgreeny on 2013-01-05
What updates did you have yesterday?  I have had none since Dec 26 here in UK, with updates done daily, as I am notified of them in my 10.04.

If you use either the update-manager or synaptic to do the updates you can see what was done from synaptic ->File ->History; if you use the terminal to upgrade packages you will need to query your system logs with ```
grep -iw upgrade /var/log/dpkg.log.1 && grep -iw upgrade /var/log/dpkg.log
```

---

### Post by steve97usa on 2013-01-05
I think I found the problem just few minutes ago.
For some strange reason after the update, Alpha tried to connect to Omega on a forbidden port.
Omega (is a server) is running failban and after the series of forbidden access it blocked Alpha !!!
Sigh, now I have to figure out what application tried the forbidden access and why !
But at least is not seems a configuration problem on Alpha ... still is quite strange !

How I can set up SOLVED on this thread ?
Or maybe I'll erase it ... I did enter in panic mode when I wrote it :)
Thanks

---

### Post by ajgreeny on 2013-01-05
No, don't erase it as it may help someone else in the same state.  YOu can mark it as solved by going to **Thread Tools** at the top of the thread, and clicking on "Mark as solved"

---

### Post by steve97usa on 2013-01-05
Ok, marked as solved.
The bottom line is, in order to solve a problem, always consider the whole system (i.e. like the network or other machines) before to enter in panic mode like I did :lolflag:

But in my defense I have to say I experienced a very peculiar set of events that brought me to point the finger on the wrong cause.
Thanks again for the patience :)

---

