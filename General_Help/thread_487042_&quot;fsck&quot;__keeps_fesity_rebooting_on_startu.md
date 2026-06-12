---
title: "&quot;fsck&quot;  keeps fesity rebooting on startup!"
date: 2007-06-28
forum: General Help
---

### Post by Jabran Asghar on 2007-06-28
Hi,

Just got a weird problem. Ubuntu was working fine on my Dell laptop, all of a sudden, After entering login information, I started getting a black screen (mouse was responsive though). Doing a restart a number of times ... the same, and then "fsck" started checking disk at boot time. 

Afterfsck finished testing, it exited with error 3 (I guess this means it found some errors and corrected them, but needed a reboot). Then it reboot automatically. After that each time I reboot, fsck starts again, exits with error code 3 and reboots ... I have tired at least 15 times!

Then I booted from Feisty Live CD, ran fsck, it said no file errors. Than I ran "badblocks" two times, that did not found any bad sectors, BUT, normal ubuntu reboot keeps looping at fsck!


I have installed no updates  (for sure, because I was not online on my laptap last 5 days and the problem just started 2 days before). Therefore, the point that some update caused this rules out.

I really do not want to reinstall Ubuntu on this Laptop as I have done lots of fine tunings of the desktop environment to my taste. I doing that again will waste a lot of time.

Any idea what is going on? and how to correct this problem. 

Jabran

---

### Post by Jose Catre-Vandis on 2007-06-28
can you boot up to a command line in recovery mode?

and then by typing "startx" bring up the root gui ?

drop back out to the command line and type:
```
fdisk - l
```
to identify where your installation is -> /dev/hd?
then type
```
tune2fs -c 1 /dev/hd?
```
where ? is the number of your ubuntu installation
type```
reboot
```
this should force fsck everytime you boot. if this clears the problem then
```
tune2fs -c 30 /dev/hd?
```
to set fsck to run every 30th boot

This approach helps to clear boot and login problems for me on occasion :)

---

### Post by Jabran Asghar on 2007-06-28
I have already tried the "Recovery" option, but "fsck" starts even in that case :-(

Any other clues?

---

