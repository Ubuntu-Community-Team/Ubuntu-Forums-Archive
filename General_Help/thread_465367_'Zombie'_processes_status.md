---
title: "'Zombie' processes status?"
date: 2007-06-05
forum: General Help
---

### Post by zodmaner on 2007-06-05
Hi, well I just check my running processes status and noticed that 'netstat' process, which is a dependency of 'firefox-bin' process, is listed as 'Zombie' in a status column. 

What is 'Zombie' status mean? Also the process use no memory and no CPU.

---

### Post by jimbob on 2007-06-05
You can't kill zombies, they are already dead.

The process is a child or fork of a parent that is long gone.  The wait system is supposed to collect all of these when a parent exits but sometimes the child is stuck in a device driver close routine or something like that.  If it remains that way forever, the device driver probably has a bug.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by zodmaner on 2007-06-05
Thanks for a quick reply! That clear things up. :)

So it is ok to have some of these zombie process, or is something wrong with my rig?

---

