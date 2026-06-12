---
title: "Recommending Wubi from GetGNULinux.org"
date: 2007-10-30
forum: General Help
---

### Post by ariadacapo on 2007-10-30
Hi,

We're a small non-profit called [GNU/Linux Matters]("http://www.gnulinuxmatters.org/") and we maintain a website called [GetGNULinux.org]("http://www.getgnulinux.org/"). It's an introduction to Linux for everyday Windows users, translated in four languages.

I've seen a demo of Wubi by René Dittmann at [Ubucon]("http://www.ubucon.de/") and I was very, very impressed. 
Since our target audience is exactly the kind of people that would want to use Wubi, we are thinking of recommending it on our pages.

We "need" two important things before we can safely send many newcomers to wubi, and this is
1. Ubuntu 7.10
but as I can see, you're working hard on this it seems ;-)
2. A little more security warning
Specifically (correct me if I'm wrong), there is nowhere written that it's recommended to de-fragment the hard drive before installing. Also, Wubi mounts NTFS partitions on the Ubuntu desktop by default with write enabled; this is rather scary...

So the goal of this email is simply to give a little encouragement (and kindly ask for a little more security precautions). We'll be really happy to promote this great way of installing Ubuntu.

Thanks, 
Olivier.

---

### Post by ago on 2007-10-31
> **ariadacapo said:**
> Since our target audience is exactly the kind of people that would want to use Wubi, we are thinking of recommending it on our pages.
Nice to hear that, thanks...

> 1. Ubuntu 7.10
Me too... There is an issue with the kernel at the moment which has been biting us since before beta and is the main reason I cannot push out a release. It's the reason why you read about freezes while copying files... No soon enough...

> Specifically (correct me if I'm wrong), there is nowhere written that it's recommended to de-fragment the hard drive before installing.
Defragmenting is recommended but not strictly necessary. What is probably more important is chkdsk /r. I will add that warning, if a chkdsk is required. 

> Also, Wubi mounts NTFS partitions on the Ubuntu desktop by default with write enabled; this is rather scary...
If you want to operate from within a file on top of an ntfs partition you need write access to the ntfs partition. There is no way around that. Anyway ntfs-3g is stable enough and write access to NTFS is enabled by default in Ubuntu, so I am not particularly concerned about that.

Any suggestion is more than welcome, feel free to add comments here or in separate posts.

---

### Post by Computer Guru on 2007-10-31
Hey, Gutsy (normal setup, not Wubi) mounted my NTFS formatted 3rd hard drive for read/write by default, and I don't even have Windows installed!

I guess that means it's stable enough?

---

### Post by ariadacapo on 2007-11-06
I aplogise for the delay in replying, I have difficulty keeping track of everyrhing... Thanks for your answer.

> Defragmenting is recommended but not strictly necessary. What is probably more important is chkdsk /r. I will add that warning, if a chkdsk is required.

That would be nice. Typically our audience here has very little computing knowledge (therefore is more likely to have a messy hard drive), and, especially, is not a risk-taker. The safest the better, even if it costs some additional minutes.
In fact, it would be ideal if Wubi did it automatically.

> 
Anyway ntfs-3g is stable enough and write access to NTFS is enabled by default in Ubuntu, so I am not particularly concerned about that.


I lack experience to give relevant feedback, but I've heard of several cases where write access to NTFS has messed up the partition.
It's ok losing a file but screwing up the whole Windows install is scary.
But again I lack relevant experience and I think you are probably right to enable write access.

Thanks again and I'll keep an eye on Wubi development; as soon as it turns stable we'll do something about it on our side of things =)

Olivier.

---

### Post by ago on 2007-11-06
People end up with corrupted a filesystem when they hardreboot... Not really a linux/wubi issue as far as I can tell...

---

