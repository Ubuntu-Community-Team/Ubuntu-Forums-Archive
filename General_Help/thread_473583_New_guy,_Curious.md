---
title: "New guy, Curious"
date: 2007-06-14
forum: General Help
---

### Post by callistek on 2007-06-14
I checked the FAQ's and everything, and didn't seem to find the response I was looking for. But I normally have a hard time understanding.

I am a beggining user, used knoppix before, but never ubuntu. And I would love to have Ubuntu and Windows Xp capabilities that wubi advertises. However, I also have a second hard drive sitting here staring at me with 2 NTSF partitions on it, both empty, one for the OS, and one for files...

I don't think it's possible, but is it possible that wubi uses my ubuntu alternate iso, to format that OS partition of my E:/ and install ubunto there, as a partition (so I can maximize speed)?


I am worried because of what somone posted saying how the normal instalation is 5x faster... well I couldn't normally install the ubuntu desktop .iso  so that is why i'm resorting to wubi.


I will go post my problem with installing with the normal way in the support area of ubuntu forums

---

### Post by ago on 2007-06-14
If you have a spare partition/disk you are better off using the live CD and do a full installation. 

As for wubi it is normall as fast as a normal installation, only under particular cases it is slower (apparently on low spec machines). None of the devs has been able to reproduce that, but as a user with a PC >3YR you should expect wubi to run more than fast enough .

---

### Post by callistek on 2007-06-14
I used the Ubuntu 7.04 Desktop i386.iso and burned a dvd-r and had many many problems trying to install (couldn't even verify disk)

that's why i'm resorting to this, I suspect it has to do with my dvd reader/hard drive combination

I have to install from a ATA dvd to a SATA hard drive (in order to use my second hard drive), however with wubi i would be installing from a mounted iso (less problems), and in my ATA hard drive ... which I imagine will have less problems.

---

### Post by ago on 2007-06-14
I would burn it on a simple CD. Also note that wubi requires the alternate ISO, the live iso will not work with it.

---

### Post by callistek on 2007-06-14
Yeah I know, that's why I'm downloading the Alternate now...

I may burn the alternate to a normal cd and try to install with that. before I try with wubi... but I really like the wubi idea, a windows installer for linux would be awsome. :P for people with crappy hardware that gives headache at least.

---

### Post by CrazyGuy123 on 2007-06-14
I was the person who had a machine 5x slower - but I also tried wubi on 4 other machines and had about the same speed I would get on a partition, so I think something might've gone wrong with that particular machine.

---

### Post by ago on 2007-06-14
> **CrazyGuy123 said:**
> I was the person who had a machine 5x slower - but I also tried wubi on 4 other machines and had about the same speed I would get on a partition, so I think something might've gone wrong with that particular machine.

Can we resume that? I cannot reproduce on my machine, hence I need some help to pinpoint the issue on your hardware. The previous feedback did not show anything particularly out of place.

---

### Post by CrazyGuy123 on 2007-06-14
Yep - no problem.  I've sort of run out of ideas as to what the problem could be though...  I could set up telnet/ssh access to it for a while if you like.

---

### Post by ago on 2007-06-14
Can you run some benchmark to see whether the bottleneck is hd I/O, cpu usage or memory? Ideally you should compare the data to a real installation on equivalent machine.

---

### Post by callistek on 2007-06-14
my problem was definatly the cd, when i burned a normal cd, it worked fine... well except for a few errors that didn't seem to compromise the install...

now i had it working for a while, before i tried to update my ati drivers, and screwed it up again... maybe i'll reinstall it again later...

---

### Post by abn91c on 2007-06-14
try moving the c:\wubi folder to the empty drive, some people is this forums had luck that way, then run the installation, just make sure you defrag all the drives and let the computer reboot by itself, **don't** do a manual reset or hard boot.If you do ubuntu may not work.

---

