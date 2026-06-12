---
title: "/var partition full"
date: 2007-02-14
forum: General Help
---

### Post by owlcroft on 2007-02-14
After receiving a popup warning message, I examined the disk list.  The /var partition is allocated 8.38 GB and apparently has zero space left.  I looked at the "Propertyies" of each folder in it and saw these data:

backup...........0
backups.........3.7 Mb
cache.........174.6 Mb
games............0    (2.1 Kb)
lib...............109.2 Mb
local...............0
lock.............473.4 Mb
log..................7.8 Mb
mail.................0
opt...................0
run...................0    (7.0 Kb)
spool................0
tmp...................0.4   (412.7 Kb)
[www.................0](www.................0)    (63.3 Kb)

Added up, that's roughly 770 Mb, maybe 3/4 Gb, not 8.38 Gb.

What can the problem be?  And what can I do to fix it?  I am ***not*** a Linux expert.

Thank you.

---

### Post by llamakc on 2007-02-14
Weird that /var/lock is so large.

Here's what mine looks like:

```

root@llamakc:/var# du -h --max-depth=1
0       ./lock
156K    ./run
5.8M    ./backups
304M    ./cache
16M     ./crash
8.0K    ./games
241M    ./lib
4.0K    ./local
70M     ./log
48M     ./mail
4.0K    ./opt
632K    ./spool
452K    ./tmp
16G     ./vm
9.9M    ./www
16G     .

```


Ignore the /vm one with 16G. That's my virtual machines. 

You can clean the apt-cache with `sudo apt-get clean` and that will free up some space.

---

### Post by dcstar on 2007-02-14
> **owlcroft said:**
> After receiving a popup warning message, I examined the disk list.  The /var partition is allocated 8.38 GB and apparently has zero space left.  I looked at the "Propertyies" of each folder in it and saw these data:

backup...........0
backups.........3.7 Mb
cache.........174.6 Mb
games............0    (2.1 Kb)
lib...............109.2 Mb
local...............0
**lock.............473.4 Mb**
log..................7.8 Mb
mail.................0
opt...................0
run...................0    (7.0 Kb)
spool................0
tmp...................0.4   (412.7 Kb)
[www.................0](www.................0)    (63.3 Kb)

Added up, that's roughly 770 Mb, maybe 3/4 Gb, not 8.38 Gb.

What can the problem be?  And what can I do to fix it?  I am ***not*** a Linux expert.

Thank you.

I have no idea why the **lock** directory is so massive, you may want to have a look in there and see what has filled it up.

Also, installing the **logrotate** package will keep your log directory under control.

---

### Post by highneko on 2007-02-14
[QUOTE="owlcroft"]The /var partition is allocated 8.38 GB and apparently has zero space left.[/QUOTE]Did you manually create a seperate partition for /var? If it's using up more space than it's saying then maybe try using sudo like in my example:
```
highneko@ubuntu:/var$ sudo du -ch --max-depth=0 /var
516M    /var
516M    total
highneko@ubuntu:/var$ 
```

---

### Post by owlcroft on 2007-02-18
Thank you all for the tips.

The du command enabled me to see that the culprit  is the /var/backup directory, which is chock-full (8.1 GB) of files with names of the general form:

  /var/backup/2007-02-01_00.00.01.91680.thisuser.inc

where "thisuser" is the userid.

Because the machine has now become altogether unusable (this post is from a separate machine on another OS), I am going to just screw my courage to the sticking place and delete all those files.  Assuming that does not destroy the system utterly, my next question is, of course, what in the world are those files?  And what is putting them there, and why?  And how do I rein it in?

Thanks again.

P.S.: Just looked again, and I see that each of those is not a file but a subdirectory.  The contetnts of one selected at random are:

base
excludes
files.tgz
flist
fprops
packages
ver

I can't glean much from looking into any of them.

---

### Post by dcstar on 2007-02-19
> **owlcroft said:**
> Thank you all for the tips.

The du command enabled me to see that the culprit  is the /var/backup directory, which is chock-full (8.1 GB) of files with names of the general form:

  /var/backup/2007-02-01_00.00.01.91680.thisuser.inc
........
 Just looked again, and I see that each of those is not a file but a subdirectory.  The contetnts of one selected at random are:

base
excludes
files.tgz
flist
fprops
packages
ver

I can't glean much from looking into any of them.

I don't recognise them myself, but is it something like sbackup running that is taking snapshots of your system on a regular basis and then saving these files?

That's about the only thing I can think of.

---

### Post by owlcroft on 2007-02-19
>[I]s it something like sbackup running that is taking snapshots of your system on a regular basis and then saving these files?

Durned if I know.  I know, in round numbers, zero  about Linux: we got this system for my lady on the theory that Linux in general and Ubuntu in particular are user-friendly and straightforward to deploy, a theory that is hideously incorrect.

Clearly, *something* is making periodic (and frequent) snapshots of some sort, but what  and why i do not know.  I'll have to look and see what was added to the initial system.

But if anyone has any ideas, based onthe format of the backup directory names, I would be most grateful for those ideas.

---

### Post by H.E. Pennypacker on 2007-06-12
Run sudo apt-get clean to remove unused packages.

---

### Post by llamakc on 2007-06-12
> **owlcroft said:**
> >[i]s it something like sbackup running that is taking snapshots of your system on a regular basis and then saving these files?

Durned if I know.  I know, in round numbers, zero  about Linux: we got this system for my lady on the theory that Linux in general and Ubuntu in particular are user-friendly and straightforward to deploy, a theory that is hideously incorrect.

Clearly, *something* is making periodic (and frequent) snapshots of some sort, but what  and why i do not know.  I'll have to look and see what was added to the initial system.

But if anyone has any ideas, based onthe format of the backup directory names, I would be most grateful for those ideas.

SOMETHING is doing what you told it to, or allowed it to do.

---

### Post by DagMan on 2007-06-12
I don't even have that directory so I'm inclined to agree that something is backing things up there.  Maybe something you installed a long time ago and forgot about.
type 
to see all current active processes
```
ps -e
```
to look at things scheduled to run at certain times by cron
```
ls /etc/*cron*
```
to look at things scheduled by crontab to run at certain times
```
crontab -l
```

---

