---
title: "Why does TOP show more than 1 user?"
date: 2012-11-17
forum: General Help
---

### Post by CosmicFlux on 2012-11-17
Hi,

I've run the TOP command in Terminal to view system processes and I have noticed that it says 4 users are logged in. I'm only logged in to one tty - tty7. 

Is this normal?


Cosmic

---

### Post by Vaphell on 2012-11-17
what does *who* say?

---

### Post by CosmicFlux on 2012-11-17
Output of TOP:

[B]top - 00:10:55 up 11:54,  5 users,  load average: 0.60, 0.35, 0.32
Tasks: 146 total,   1 running, 145 sleeping,   0 stopped,   0 zombie
%Cpu(s):  6.3 us,  1.7 sy,  0.0 ni, 90.9 id,  0.9 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem:   3872396 total,  1506384 used,  2366012 free,   156724 buffers
KiB Swap:  3923964 total,        0 used,  3923964 free,   905548 cached
[/B]

Output of WHO:

[B]daz      pts/1        2012-11-18 00:10 (:1)
daz      tty7         2012-11-17 23:49 (:1)
[/B]

---

### Post by jerome1232 on 2012-11-17
Every terminal you open is a new pts, open 4 terminals you'll have 5 users logged in

---

### Post by CosmicFlux on 2012-11-17
I only have a single terminal open, though. I've opened others and, yes, the # of users increases.  But when I close them all I'm still left with the 5 users showing on the single remaining terminal.

---

### Post by diesch on 2012-11-17
Usually there are a few processes running as system users, like *root* or *nobody*. Five doesn't seem to be unusual (it's 17 here).

```
ps ahxo user| sort -u
``` lists all users currently running processes.

---

### Post by bab1 on 2012-11-17
> **CosmicFlux said:**
> I only have a single terminal open, though. I've opened others and, yes, the # of users increases.  But when I close them all I'm still left with the 5 users showing on the single remaining terminal.

The users do not have to be logged in users (mortal users) they can be system users too.  Root is one of those so is syslog, avahi and messageb on my machine.

---

### Post by Doug S on 2012-11-17
Interesting thread. I only run Ubuntu server editions, no GUI stuff.
I have never seen "top" or "uptime" show a different number of users than "who" . I get many listed with the command diesch listed above. So maybe it some GUI desktop thing.

---

### Post by CharlesA on 2012-11-17
> **Doug S said:**
> Interesting thread. I only run Ubuntu server editions, no GUI stuff.
I have never seen "top" or "uptime" show a different number of users than "who" . I get many listed with the command diesch listed above. So maybe it some GUI desktop thing.
You and me both then.

I've run both Server and Desktop versions of Ubuntu and I've always seen the output of top in regards to users being the same as the output of who.

Intersting.

---

### Post by jerome1232 on 2012-11-18
+1

I'm fairly certain top uses 'w' to figure out how many users are logged in.

---

### Post by Doug S on 2012-11-18
What do you get for the output of "users"?
 
See also: [http://ubuntuforums.org/showthread.php?p=11670344](http://ubuntuforums.org/showthread.php?p=11670344)

---

