---
title: "Partitioning Error"
date: 2007-08-27
forum: General Help
---

### Post by rohan182 on 2007-08-27
Hi all, 

i kinda stuffed up my partitioning on my laptop hard drive when installing Ubuntu 7.04.

i used the guided system to Dual boot with XP Pro, and thought it asked me to tell it how big to make the new partition for ubuntu and i made it what i thought to be "25gig".

But infact i made my Windows partition 25gig. Which is the opposite I wanted..

I have:
TOTAL=120gig
WinXP=25gig
ubuntu=95gig

i wanted:

TOTAL=120gig
WinXP = 95
ubuntu=25gig

(i know this aint exact cause of hard drives when partitioned arn't exactly 120gig)

is there anyway i can fix this without having to use my recovery cd?


Thanks in advance

---

### Post by merlinus on 2007-08-27
You can use gparted live cd to resize.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

But then your UUIDs will change, and you will have to edit /etc/fstab to relect this.

-merlin

---

