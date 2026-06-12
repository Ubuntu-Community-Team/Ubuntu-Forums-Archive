---
title: "Is it possible to enable Hibernate without the need for Swap?"
date: 2008-02-04
forum: General Help
---

### Post by TWO on 2008-02-04
When I installed Ubuntu a while back now I did so without partitioning for a Swap drive. 

(This was all down to my reluctance to delete the Dell partition...)

Anyway, subsequently I cannot use the Hibernate function. Attempting to do so makes the screen flicker several times (and possibly brings up an error message too.) Point being, I cannot use the Hibernate function. Is there a way to enable this without a swap drive and if not, do you recommend that I repartition for it?

Thanks

---

### Post by dcstar on 2008-02-04
> **TWO said:**
> When I installed Ubuntu a while back now I did so without partitioning for a Swap drive. 

(This was all down to my reluctance to delete the Dell partition...)

Anyway, subsequently I cannot use the Hibernate function. Attempting to do so makes the screen flicker several times (and possibly brings up an error message too.) Point being, I cannot use the Hibernate function. Is there a way to enable this without a swap drive and if not, do you recommend that I repartition for it?


Since the Hibernate function uses the Swap partition to store a snapshot of the running memory, no.

Just boot off the Live CD and repartition/move your existing stuff to make room for a swap partition (as big as your installed RAM), then enable that swap partition.

---

### Post by TWO on 2008-02-04
> **dcstar said:**
> Since the Hibernate function uses the Swap partition to store a snapshot of the running memory, no.

Just boot off the Live CD and repartition/move your existing stuff to make room for a swap partition (as big as your installed RAM), then enable that swap partition.

OK then,Thank you.  I'll just go ahead and re-partition.

TWO

---

### Post by Rocket2DMn on 2008-02-04
You will need to use the LiveCD to access GParted which will enable you to resize your partitions.  You can install GParted from the repos and use it on other drives, but the LiveCD is needed this time because you are fiddling with your root partition and can't do that unless it's unmounted.
From the LiveCD: System->Administration->Partition Editor
If you don't have a LiveCD, you can also use the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by TWO on 2008-02-04
> **Rocket2DMn said:**
> You will need to use the LiveCD to access GParted which will enable you to resize your partitions.  You can install GParted from the repos and use it on other drives, but the LiveCD is needed this time because you are fiddling with your root partition and can't do that unless it's unmounted.
From the LiveCD: System->Administration->Partition Editor
If you don't have a LiveCD, you can also use the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Yeah, I have a Live CD that I made a little while back. Thanks for your suggestion!

---

### Post by pointone on 2008-02-04
It should be possible to simply configure Ubuntu to use a swap file instead of a swap partition. This would eliminate the need for re-partitioning.

[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

---

### Post by TWO on 2008-02-05
> **pointone said:**
> It should be possible to simply configure Ubuntu to use a swap file instead of a swap partition. This would eliminate the need for re-partitioning.

[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

That sounds like an even more convenient way. However, the article does say: > The hibernation implementation currently used in Ubuntu, swsusp, needs a swap or suspend partition, and can not use a swap file on an active file system.

This is one of the reasons I want to enable Swap and then obviously as a compliment to the RAM. 

(Unless it is now possible for Hibernation to implemented via a Swap file ?)

---

### Post by TWO on 2008-02-05
Looks like the statement on that page was true since after having set up a  Swap file, the HIbernate option has disappeared from the Shut down menu...

---

### Post by jsnelli2 on 2008-02-05
This may only be for speed purposes, but shouldn't the swap file be twice the size of the RAM you have in your computer instead of just the size of it?  It probably wouldn't make a difference for hibernate though I suppose.

---

### Post by TWO on 2008-02-10
> **jsnelli2 said:**
> This may only be for speed purposes, but shouldn't the swap file be twice the size of the RAM you have in your computer instead of just the size of it?  It probably wouldn't make a difference for hibernate though I suppose.

Yeah, apparently something like that. 

 I think I may just go ahead and repartition because I would like to have Hibernate as an option.

---

