---
title: "disk usage info seems strange"
date: 2005-10-18
forum: General Help
---

### Post by scoonk on 2005-10-18
Hi, 
this may seem like a stupid question, but im missing 6GB on my ext2 fs on
SATA disk partition

terminal>

scoonk@scoonk:~$ df -h

Filesystem            Size    Used  Avail  Use% Mounted on
/dev/sda5             128G  121G  154M 100% /media/sam140


any sugestions?

---

### Post by megamania on 2005-10-22
[QUOTE=scoonk]

Filesystem            Size    Used  Avail  Use% Mounted on
/dev/sda5             128G  121G  154M 100% /media/sam140
[/QUOTE]

same problem here:

df --si /home
Filesystem            Size    Used  Avail  Use% Mounted on
/dev/hda6              144G   134G   2,4G  99% /home

...hope somebody has a clue as I'm really curious...

---

### Post by megamania on 2005-10-23
Well, I checked my Linux bible (should have done that before) and saw that a part of disk space is "blocked" and reserved for superuser (to avoid system crashes due to sudden "disk full" errors). This appears to be useful mostly for servers though.

My question now is if there's a way to make at least part of this space available, otherwise I'll have to buy a bigger hard disk...   :-|

---

### Post by scoonk on 2005-10-24
Hi again and thanks Megamania!
the reason of the problem is that the system at installation reserves 5% of each partition for itself. But still I'm unable to change this. Going to update to 5.10, hope to solve it there. But if you find a way to change the amount of reserved space recursively in Hoary, please answer.

Thanks, and once again thanks in advance!

---

### Post by megamania on 2005-10-26
Well, yes I kind of sorted this out. try:

sudo tune2fs -m 0 /home   (change /home to your mount directory, if different)

this will reduce to zero the reserved space. Please note that you shouldn't use it on a mounted hd and you are supposed to boot in single user mode.

I did it on a mounted hd (/home) with no problems, but be warned and check the man page (man tune2fs) as (1) I'm an absolute beginner and (2) I had a FULL backup of my data!

Ciao!

---

### Post by scoonk on 2005-10-29
Hi and thanks again!
It worked perfectly.

You can adjust and setup everything in Linux, but smtms really hard to find how...

---

