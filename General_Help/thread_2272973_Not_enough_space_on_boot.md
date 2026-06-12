---
title: "Not enough space on /boot ?"
date: 2015-04-09
forum: General Help
---

### Post by Punk_A_Cat on 2015-04-09
The automatic update is telling me there isn't enough room on /boot, I've run sudo apt-get clean, and it's had no effect. How do I increase the boot size so I can install the update?
Running Ubuntu 14.4 stable, with a 320 hard drive, which isn't even close to full, the filesystem/boot partition is 78.2% full though?

---

### Post by Bashing-om on 2015-04-09
Punk_A_Cat; Hello;

> **Punk_A_Cat said:**
> The automatic update is telling me there isn't enough room on /boot, I've run sudo apt-get clean, and it's had no effect. How do I increase the boot size so I can install the update?
Running Ubuntu 14.4 stable, with a 320 hard drive, which isn't even close to full, the filesystem/boot partition is 78.2% full though?

LVM ? encryption ? perhaps:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1357093)
refers ?

Try the command :
```

sudo apt-get autoremove

```
to remove the old kernels.
See now if you can update:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
[INDENT][INDENT][INDENT]maybe YES
[/INDENT][/INDENT][/INDENT]

---

### Post by Punk_A_Cat on 2015-04-09
Thanks, it has let me update now. Any way to actually increase the size of the /boot though? seems like this will be an ongoing problem.

---

### Post by Bashing-om on 2015-04-09
Punk_A_Cat; Well ...

This is 'buntu, there is always a way .. but is the cost worth it ?
While one can repartition it is a hassle and a great risk of data loss - one should back up all their data prior to re-partitioning. It is a small matter to keep an eye on /boot and when new kernels are installed, 'autoremove' the old kernels.

The choice is yours . -> I think personal system management is the better option.

[INDENT][INDENT]just because I do
[INDENT][INDENT][INDENT]is not to say it is always right to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Punk_A_Cat on 2015-04-09
Ok, cool, I wasn't sure if cleaning and auto removing on a regular basis would be enough, but if it will that's fine. Thanks so much :)

---

### Post by Bashing-om on 2015-04-09
Punk_A_Cat; Yeyah;

That will be good 'nuf .
Package manager is cool, huh ?

[INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

