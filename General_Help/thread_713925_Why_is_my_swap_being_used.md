---
title: "Why is my swap being used?"
date: 2008-03-03
forum: General Help
---

### Post by ~LoKe on 2008-03-03
> (~) //-> free
             total       used       free     shared    buffers     cached
Mem:       2074556    1990064      84492          0      36956    1558468
-/+ buffers/cache:     394640    1679916
Swap:       514072      38736     475336

With 2GB of ram and only Firefox, MPD and Screen running, I shouldn't be hitting the swap partition.  Where should I start diagnosing the problem?

---

### Post by OrangeCrate on 2008-03-03
This will help you to understand how Linux manages memory:

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by ~LoKe on 2008-03-03
> **OrangeCrate said:**
> This will help you to understand how Linux manages memory:

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

I noticed a while back that most free memory is just cached so it appears as if it's all being used, but that doesn't quite apply here.  I have 2GB of memory, and somehow only a few applications are making their way to my swap.  This shouldn't happen.

---

### Post by SunnyRabbiera on 2008-03-03
well I too see swap being used despite the fact I am running at one gig.
But I think its a good thing that there is some swap to work with just in case there is a major hangup, swap comes in handy during updates...

---

### Post by ~LoKe on 2008-03-03
It's nice to **have** swap available, but it's using your hard drive as RAM which means a huge hit in performance.

---

### Post by frodon on 2008-03-03
You can disable swap if you don't want to swap, with 2Gb of RAM it's not a problem. I confirm you that it is normal that your swap is being used as it is how ubuntu is configured by default and this as nothing to do with how many memory you have, in addition that don't really matter IMO because most used datas are saved in RAM so you shouldn't even notice any speed difference.

If you want to modify how your ubuntu install use swap play with the swapiness parameter, it is really well explained in the link given by OrangeCrate.

---

### Post by Oldsoldier2003 on 2008-03-03
> **~LoKe said:**
> I noticed a while back that most free memory is just cached so it appears as if it's all being used, but that doesn't quite apply here.  I have 2GB of memory, and somehow only a few applications are making their way to my swap.  This shouldn't happen.
I agree with that, unless you are running some huge applications your swap should barely ever be touched. Even when compiling apps and running firefox,gimp,xara. bluefish,filezilla, wine pidgin and several more terminals simultaneously i never touch the swap on my 1GB desktop machine. Seems odd you would be...

---

### Post by SunnyRabbiera on 2008-03-03
> **~LoKe said:**
> It's nice to **have** swap available, but it's using your hard drive as RAM which means a huge hit in performance.

not in my case, when I had a smaller amount of ram swap was a lifesaver

---

### Post by ung/xunil on 2008-03-03
I have 1,5 GB RAM and it happens here also. It seems that the 38 MB is all that is used here also.

```
             total       used       free     shared    buffers     cached
Mem:       1554996    1406472     148524          0         40     929364
-/+ buffers/cache:     477068    1077928
Swap:      2562328      **38344**    2523984

```

Apparently it is as frodon is saying. Swap isn't really being used. 

Deactivating the swap would be a option to not use swap at all, but one time something happen and swap saved me. While downloading mail in evolution, spamassassin went crazy once, and started eating up all my memory and then it started eating all my swap (2.5 GB!) - I saw this live from "gnome-monitor" in my gnome-panel... If I had no swap, the computer would have freeze before I had the chance to kill the spamassassin process, so I leave it there as a buffer for cases like this.

---

### Post by Oldsoldier2003 on 2008-03-03
> **ung/xunil said:**
> I have 1,5 GB RAM and it happens here also. It seems that the 38 MB is all that is used here also.

```
             total       used       free     shared    buffers     cached
Mem:       1554996    1406472     148524          0         40     929364
-/+ buffers/cache:     477068    1077928
Swap:      2562328      **38344**    2523984

```

Apparently it is as frodon is saying. Swap isn't really being used. 

Deactivating the swap would be a option to not use swap at all, but one time something happen and swap saved me. While downloading mail in evolution, spamassassin went crazy once, and started eating up all my memory and then it started eating all my swap (2.5 GB!) - I saw this live from "gnome-monitor" in my gnome-panel... If I had no swap, the computer would have freeze before I had the chance to kill the spamassassin process, so I leave it there as a buffer for cases like this.

Yeah, plus honestly the space used by the swap file is negligible when you consider the capacity of HDDs now.  Now im curious... maybe i adjusted the swappiness on this machine a long time ago and forgot about it...

edit: hm swappines is 60 either i changed it back or the Gutsy upgrade did.

---

