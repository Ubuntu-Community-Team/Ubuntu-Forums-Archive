---
title: "System Monitor vs Gparted"
date: 2016-09-29
forum: General Help
---

### Post by bookie2 on 2016-09-29
Hi guys!
Installed System Monitor to keep track of my services...but it says full on a partition that gparted says pleanty of space?
Any ideas?

bookie32

---

### Post by howefield on 2016-09-29
What does

```
df -h
```

say about your mounted file systems and a screenshot of System Monitor might be helpful.

---

### Post by bookie2 on 2016-09-29
Hi howefield:D
OK! I removed some files from that drive and System Monitor is registering that fact:

df -h says...
System Monitor says..
Gparted says...
Gparted all drives...
I hope that helps

---

### Post by howefield on 2016-09-29
So no problem then ?

The Virtual Machines disk which System Monitor says is (almost) full is in fact, almost full.

---

### Post by bookie2 on 2016-09-29
Sorry, forgot the pics are in Swedish...
Gparted says I have 76.81 GB unused where as System Monitor says 32.4 or am I missing something here?

bookie32

---

### Post by bookie2 on 2016-09-29
Hi again!
Just a little update...
I was worried that something was wrong with gparted on my system, so I ran gparted live cd to check output...exactly as the one installed on my computer....just don¨t understand this at all...

bookie32

---

### Post by howefield on 2016-09-29
I think it will be the system reserving 5% of ext partitions for use by the root account.

Gparted is showing the total used/available whereas the other applications take account of this 5%, around 40 ish GB in your case. The amount of space that is reserved by the system can be tuned but I'd generally recommend against doing that unless you were fully aware of the consequences.

PS. Terminal output is generally best copy/pasted between code tags, rather than posted as an image, not so much in this thread but for future threads.

---

### Post by bookie2 on 2016-09-29
Hi howefield:D
Thanks for the info...have been reading up on it...just never really noticed it before....
Thanks again for all help!
bookie32

---

