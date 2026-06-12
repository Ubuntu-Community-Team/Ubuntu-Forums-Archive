---
title: "Help understanding high cpu usage on server"
date: 2007-12-03
forum: General Help
---

### Post by mikecrowe on 2007-12-03
Hi folks,

My monitoring program, zabbix, is reporting what I think is unusually high cpu usage on one of my virtual machines.  In theory, there should be little running on this server at this time.

When I do a top command, it looks fine.  Nothing jumps out.

What is available to help me troubleshoot?  Ideally, I'd love a program which takes the top of top and gathers that data for 1h or so.

Anything like that exist?

TIA
Mike

---

### Post by p_quarles on 2007-12-03
This could be a simple case of Zabbix getting the numbers wrong. On the other hand, if this is a public server -- well, a rootkit could easily have changed the output of top to cover its tracks. 

Here are some things to do:
1) Run "top" on the host system
2) If you have a snapshot of the VM before it started doing this, restore it. Does the problem go away?
3) Monitor network activity on the system.

---

### Post by mikecrowe on 2007-12-03
I think you miss what I'm asking for:  top is an instantaneous tool, and nothing is immediately obvious.  I would like something that give me the top cpu consumers over a 1h period (for example)

---

### Post by p_quarles on 2007-12-03
Actually, you asked for "what is available to help me troubleshoot," and I offered several examples. 

But, you can get the cumulative CPU times for all apps by running:
```
ps -aux
```
Likewise,
```
top -S
```
Will add cumulative CPU time to the displayed columns.

---

