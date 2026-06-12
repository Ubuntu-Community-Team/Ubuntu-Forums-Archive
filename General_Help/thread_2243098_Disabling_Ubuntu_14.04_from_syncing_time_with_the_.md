---
title: "Disabling Ubuntu 14.04 from syncing time with the hardwae clock"
date: 2014-09-06
forum: General Help
---

### Post by adromidon on 2014-09-06
I have seen this issue before but I can not seem to find it after searching, I installed Ubuntu 14.04 on a set of eSATA drives which works great but when I reboot into Windows ( yes I need both) the time is all messed up, I am aware this is due to Ubuntu converting time to UTC then syncing it to the hardware clock at some point during use.

What I would like to know is simply how to disable Ubuntu from syncing with the hardware clock to prevent this issue.

I know its possible (i did it a while back as I said had seen this on here before) but not sure the command neccessary to do it. I am comfortable using the Command Line enough to use a command there to disable if neccessary.

---

### Post by Irihapeti on 2014-09-06
I don't know how to get Ubuntu from syncing the time at all, but I do know how to get it to use local time instead of UTC, which effectively does the same job.

You need to edit the file /etc/default/rcS

It's a text file, so use your preferred editor as root.

e.g.
```
sudo nano /etc/default/rcS
```

Change the line that says:

```
UTC=yes
```
to
```
UTC=no
```

Save and quit.

You'll need to reboot for the change to take effect.

---

### Post by adromidon on 2014-09-10
> **Irihapeti said:**
> I don't know how to get Ubuntu from syncing the time at all, but I do know how to get it to use local time instead of UTC, which effectively does the same job.

You need to edit the file /etc/default/rcS

It's a text file, so use your preferred editor as root.

e.g.
```
sudo nano /etc/default/rcS
```

Change the line that says:

```
UTC=yes
```
to
```
UTC=no
```

Save and quit.

You'll need to reboot for the change to take effect.
Thanks I will try it

---

