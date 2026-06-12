---
title: "Return Ubuntu partion back to Vista"
date: 2008-06-18
forum: General Help
---

### Post by KerPlop on 2008-06-18
Hello all,

Sorry that my first post can't be about a positive experience with Ubuntu. I got it running on my labtop and found it too much of a hassle to set up my wireless connection. I decided to delete the partition and stick with Vista.

The problem is I can't for the life of me figure out how to return the old ubuntu partition to Vista. All the help I found online (including this very forum) explains several methods but not in a way that can be easily understood by your average Joe.

I've tried using Vista's Computer Management but am unsure how to use it. Likewise, I read GParted will work like Partition Magic, but I see no step-by-step guides on how to merge partitions. Please Help!:(

---

### Post by etnlIcarus on 2008-06-19
If I remember correctly, you merely have to delete your ext3 and swap partitions; resize the NTFS one and set it as the primary partition. Gparted is pretty self-explanatory so if you're having trouble, you'll have to give specific details.

However, you have to do this from a LiveCD. If you're in Ubuntu or Windows (god forbid you use Windows partitioning tools) when you do this, it won't work. Just make sure you're booting from the Ubuntu LiveCD you used to install the OS in the first place.

---

### Post by bodhi.zazen on 2008-06-19
[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

    wubi : [https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d](https://wiki.ubuntu.com/WubiGuide#head-7cd5a1eda23f1e9960c28ef3a2f4e8645c5ea87d)

---

### Post by KerPlop on 2008-06-19
First, thanks for answering my question so quickly. I've heard these forums were very active but didn't really expect an response until morning.

Originally I did attempt to resize the Vista partition using the Partition Manager from Ubuntu's Live CD.

From there I wasn't sure what I should do to remove Ubuntu. I've been reluctant to try GParted because screen shots of it appear the same as what is on the live CD.

I guess I'll give it another shot and try to post details of where I get lost. If this doesn't work I might just have to cough up the dough for Partition Magic or take it to a "professional" and have them do it.

---

### Post by etnlIcarus on 2008-06-19
I wouldn't advise taking your PC to a store. If you know someone who can fix it for you, by all means but PC stores are likely to rip you off. They'll probably try to charge you for a new copy of Vista.

---

