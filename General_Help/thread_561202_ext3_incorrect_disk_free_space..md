---
title: "ext3 incorrect disk free space."
date: 2007-09-27
forum: General Help
---

### Post by richjoyce on 2007-09-27
Hi everyone,

I have an external 250GB (by the manufacturer) hard drive that should be 230GB.  I have it formatted with just one ext3 partition for the entire disk. Now I fill it up with tons of stuff, and here is my df -h output:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              19G   14G  3.6G  80% /
...(Other partition info removed)...
/dev/sdc1             230G  214G  4.3G  99% /media/Demeter
```

so /dev/sdc1 shows a size of 230 GB, and it says Used 214GB and 4.3GB free.  214GB + 4.3GB != 230GB, so where is my missing 12 gigs!?  Gparted says that I have 16GB unused, but I can't write to it once I use up this 4GB.

I've run fsck.ext3 on it, and it says its clean.  What is wrong with it?

---

### Post by Steveway on 2007-09-27
The ext3 filesystem takes about 5, or were it 10?, percent for itself so it will be still usable when it gets very full.
If you did your homework and used Google and Wikipedia then you would know this.

---

### Post by richjoyce on 2007-09-27
Ok, now knowing this, I was able to find some help on my actual problem:
[http://forum.mandriva.com/viewtopic.php?p=360256&sid=e2b387f366911d32a714afd46c3c89d8](http://forum.mandriva.com/viewtopic.php?p=360256&sid=e2b387f366911d32a714afd46c3c89d8)

Suggests that I should run tunefs to change the amount reserved for root, since I don't think root needs 12.5GB's on a data hard drive.
# tune2fs -m 0 /dev/sdc1

Doing this solved my problem and df -h now reads:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             230G  214G   16G  94% /media/Demeter
```

Thanks for the help and the insult to my intelligence.

---

### Post by Steveway on 2007-09-27
No Problem.
It was no insult against your intelligence, I reminded you of what you should have done.
If every second person on this board did a little check before he posted a question then this board would be pretty empty.

---

### Post by nowshining on 2007-11-01
> **Steveway said:**
> No Problem.
It was no insult against your intelligence, I reminded you of what you should have done.
If every second person on this board did a little check before he posted a question then this board would be pretty empty.

so very true. :)

---

### Post by YetiCGN on 2008-07-24
You forget one thing when you only refer people to Google and Wikipedia (where is this topic in WP, btw?): Forums also serve as a knowledge base and people like me can find answers to their problems by using "Google" ;) to get to this post and find help.

More often than not you get frustrated if you are searching for an answer to your problem and the first 10 search hits are "rtfm" or not answered at all.

So keep up the answering, helped me a lot!
But even 1% was too much on my 750 GB hard drive and .x percentages can be set but always results in 0 blocks being reserved. So I used tune2fs -r 500000, which reserves 2 GB (as in billion bytes).

---

