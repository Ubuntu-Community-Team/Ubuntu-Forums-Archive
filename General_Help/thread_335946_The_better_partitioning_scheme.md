---
title: "The better partitioning scheme?"
date: 2007-01-11
forum: General Help
---

### Post by renatosilva on 2007-01-11
Guys I'm planning what to do with my 160GB of HD regarding partitioning and distros installing. What are your suggestions? I'm planning to keep Fedora, Kurumim and Ubuntu in disk, and maybe leave free space for some issue.

1) I know I can share swap between distros, and I guess 512MB for my 1GB RAM is fine. Really?

2) What the advantages of creating another partitions besides swap for a single system? e.g. one for /home, for /boot, for /var etc. I can't see any motivation to do so, except wheter I'll be able to share another partitions such as /home, /var, don't know...Is it possible?

3) Should I put all my documents, e.g. a lot of music and video, into my home dir? I've created a /data partition and plan to keep my docs there, leaving /home only as a configuration profile...Are you for?

5) What's the size recommended for "/" partition? By now Fedora has 10GB, and /data has 40GB, and Kurumim has 5GB. I was thinking wether 5GB fits well for Ubuntu. What are the aspects involved? 

6) What's the order of partitions recommended? Swap first, then root, then /data, or another set? Currently I have 10GB for Fedora firts, then 40GB for /data, then 512MB for swap, then 5GB for Kurumim and finally 95GB of remaining space, maybe for Ubuntu. What scheme?

7) /data is shareable among distros? For example Fedora doesn't seems to support reiserfs. What about the permissions? The owner or group of a file can exist in one system but not in other, however being referenced on that /data file system.

8 ) What partition should be primary and what should be logical (under extended)? Roots should be primary and swap be logical? Or what?

Note that I can erase all my disk so I can reorganize in any way and install all distros again. It's no problem. Note: 8 questions, I'll be happy if I found answered. :p 

Thanks and answer!

---

### Post by bodhi.zazen on 2007-01-11
It's a matter of style and ther is more then 1 way to skin a cat.

This is what I thing:

[http://ubuntuforums.org/showthread.php?&t=300246](http://ubuntuforums.org/showthread.php?&t=300246)

Posts # 10 and 13

As far as permissinos, If you use Ext3 in your /data partition you should be just fine.

Set permissions to 777, 770 if you are more paranoid. Just make sure the data partition is owned by the group users.

---

### Post by Elim on 2007-01-11
> **renatosilva said:**
> 
1) I know I can share swap between distros, and I guess 512MB for my 1GB RAM is fine. Really?


Hmm.  Well, in my mind it depends on two things.  First, do you really need your hdd space, or can you easily part with another 512 MB (1 GB swap would be my preference).  Second, do you often use applications that use a lot of RAM?

> 
3) Should I put all my documents, e.g. a lot of music and video, into my home dir? I've created a /data partition and plan to keep my docs there, leaving /home only as a configuration profile...Are you for?


It seems more logical to me to put all of it in the /data partition.  As you are, I am currently planning my hdd partitioning scheme!  (I'm typing this from a Live CD.)  I planned to have a /data partition with all my music and docs, unless someone comes up with a compelling reason to stick it on a /home partition.

> 
5) What's the size recommended for "/" partition? By now Fedora has 10GB, and /data has 40GB, and Kurumim has 5GB. I was thinking wether 5GB fits well for Ubuntu. What are the aspects involved? 


This most likely depends on how many apps you d/l and install.  I'm planning mine with 15 GB / partitions, but I also have a lot of space.

> 
6) What's the order of partitions recommended? Swap first, then root, then /data, or another set? Currently I have 10GB for Fedora firts, then 40GB for /data, then 512MB for swap, then 5GB for Kurumim and finally 95GB of remaining space, maybe for Ubuntu. What scheme?


Good question.  I would be interested in hearing the answer, but I do not know it.

> 
7) /data is shareable among distros? For example Fedora doesn't seems to support reiserfs. What about the permissions? The owner or group of a file can exist in one system but not in other, however being referenced on that /data file system.


I believe all distros can read ext3, so I would recommend using that, at the very least for /data.  If I may be allowed to derail the thread for a moment, why do you use reiserfs instead of ext3?

> 
8 ) What partition should be primary and what should be logical (under extended)? Roots should be primary and swap be logical? Or what?

Another good question that I'd like the answer to.  I'm currently planning a very similar setup: 3, maybe 4 / partitions, a /data partition, and a swap partition.  However, I know nothing about extended partitioning.  Does anyone have any tutorials or links on extended partitioning, especially pertaining to installing Win XP on one of the partitions?

---

### Post by bodhi.zazen on 2007-01-11
Some OS, Windows and BSD, can only go onto primary partitions.

Linux is more flexible this way so primary/extended does not matter.

On a disk you can only have 4 primary partitions.

To overcome this limitation one makes an extended partition.

An extended partition is then sub-divided into logical partitions. You may have a large number of logical partitions in a large extended partition.

HTH

You can also look at this if you like:


[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by Toet on 2007-01-11
> **renatosilva said:**
> 
6) What's the order of partitions recommended? Swap first, then root, then /data, or another set? Currently I have 10GB for Fedora firts, then 40GB for /data, then 512MB for swap, then 5GB for Kurumim and finally 95GB of remaining space, maybe for Ubuntu. What scheme?


The disk starts at the inner side working outwards. So the first partition is the fastest. Personally I always set it up to have swap first then root then home.

---

### Post by renatosilva on 2007-01-11
Thank you guys! You are helping me very much! Comments is welcome still...

---

### Post by Elim on 2007-01-11
> **bodhi.zazen said:**
> 
You can also look at this if you like:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

That's an excellent guide, bodhi, thanks a lot for writing it!  It helped immensely.  As most good guides do, however, it introduced new questions even as it answered some old ones.

First, three simple questions:

1.) Can BSD use a swap that's on an extended partition?

2.) Can Win or BSD read/write to a data partition that's on an extended partition, or do I need to put my data partition on a primary partition?

3.) Is there any advantage to having an OS on a primary partition as opposed to an extended partition?

Finally, two slightly more complex ones:

4.) According to Wikipedia, "by using a separate swap partition, it can be guaranteed that the swap region is at the fastest location of the disk. On current HDDs this is the beginning."  So should swap be primary partition 2 (since 1 has to be Windows, I think)?  Does it make much of a difference?

5.) "My advice is to always put your FreeBSD slice after any Linux extended partitions, and do not change any logical partitions in your Linux extended partitions after installing FreeBSD!" -- Source: [http://www.faqs.org/docs/Linux-mini/Linux+FreeBSD.html](http://www.faqs.org/docs/Linux-mini/Linux+FreeBSD.html)
That doc was written in 2000; does that piece of advice still apply?

I think I would use one of the following partitioning setups depending upon the answers to those questions:

Primary 1 = Windows
Primary 2 = Extended
	Linux1
	Linux2
	swap
Primary 3 = BSD
Primary 4 = data

OR

Primary 1 = Windows
Primary 2 = swap
Primary 3 = Extended
	Linux1
	Linux2
	data
Primary 4 = BSD

---

### Post by bodhi.zazen on 2007-01-11
> **Elim said:**
> That's an excellent guide, bodhi, thanks a lot for writing it!  It helped immensely.  As most good guides do, however, it introduced new questions even as it answered some old ones.

First, three simple questions:

Hmm ...

> 1.) Can BSD use a swap that's on an extended partition?

Yes.

> 2.) Can Win or BSD read/write to a data partition that's on an extended partition, or do I need to put my data partition on a primary partition?

Yes both Windoz and BSD can read data on extended partitions. It is only the root file system that needs to be on a primary partition.

> 3.) Is there any advantage to having an OS on a primary partition as opposed to an extended partition?

IMO, no.

> Finally, two slightly more complex ones:

4.) According to Wikipedia, "by using a separate swap partition, it can be guaranteed that the swap region is at the fastest location of the disk. On current HDDs this is the beginning."  So should swap be primary partition 2 (since 1 has to be Windows, I think)?  Does it make much of a difference?

This is accurate information, however nowadays with increasing RAM the swap partition is not accessed as much.

Overall you will not likely notice much if a difference in performance.

> 5.) "My advice is to always put your FreeBSD slice after any Linux extended partitions, and do not change any logical partitions in your Linux extended partitions after installing FreeBSD!" -- Source: [http://www.faqs.org/docs/Linux-mini/Linux+FreeBSD.html](http://www.faqs.org/docs/Linux-mini/Linux+FreeBSD.html)
That doc was written in 2000; does that piece of advice still apply?

I think this is an opinion rather then absolute advice ....

However, If you re-partition ("change any logical partitions") you will need to update grub and fstab ...

> I think I would use one of the following partitioning setups depending upon the answers to those questions:

Primary 1 = Windows
Primary 2 = Extended
	Linux1
	Linux2
	swap
Primary 3 = BSD
Primary 4 = data

OR

Primary 1 = Windows
Primary 2 = swap
Primary 3 = Extended
	Linux1
	Linux2
	data
Primary 4 = BSD

This is what I do:

Primary 1 Free BSD
Primary 2 Linux or BSD
Primary 3 Linux or BSD

Primary 4 Extended
[indent]The partitions below are all "Logical"[/indent]
[list][*]Linux 1
[*]Linux 2
[*] ...
[*]swap
[*]Data[/list]

Works just fine, can share data and swap between OS.

I do not notice any lack of performance.

I do not run Windows, but in the past had no problems with windows in Primary 1 ...

---

### Post by Elim on 2007-01-11
bodhi, you're a lifesaver!  Thanks for all your help!

---

### Post by yopnono on 2007-01-11
> **Toet said:**
> The disk starts at the inner side working outwards. So the first partition is the fastest. Personally I always set it up to have swap first then root then home.

Why have the swap as first partition? are you using the swap a lot.
I would prefer to have the OS at 1st partition, and swap last.

---

### Post by renatosilva on 2007-01-11
Another reason to keep the system root in one '/' partition is that accessing data on other partitions is slower, I can see this on Windows and have heard about it as a general issue.

---

### Post by dabl on 2007-01-11
I just installed Kubuntu Edgy on a new 150GB hdd (it formatted out at about 149).  I had a lot of data to bring over from my Windows box, and it will grow, so I wanted that in a safe place.  First, I read this nice dissertation for newbies:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Then I partitioned as follows:

/ = 10
/home = 135
/{swap} = 4

That was in early December.  I now find root is 40% full, and that's after I cleaned out /TMP.  So, if I had used only 5GB, as you propose, I guess it would be 80% full.  You might want to consider making your root a little larger to be ultra-safe.

On the other hand, even though I have 4GB of memory installed, everything I can find, including watching my system's statistics, indicates I wasted 2GB in that 4GB swap partition, so if I were doing it over, I would make it only 2GB for swap.

:)

---

### Post by Omnios on 2007-01-11
I hate to say this as I learnt this from windows in that I have a tri boot with a small XP partition. A Fedora partition and a document partition on my main drive an Ubuntu on my 40 gig drive that seems ok for now. 

 Now the power of this is not that I have a win doc partition but rather a document partition seperate from the distros yet accessible by all the distros without having to worry about distro config files. 

 Anyway you look at it its a win win formula.

---

### Post by bodhi.zazen on 2007-01-11
Swap should be RAM X 2 ; 1 Gb max

The more ram you have, the less swap you need ...

---

### Post by dabl on 2007-01-11
Yep -- so quick to adopt, so slow to learn .... :( 

However, if that's the worst problem with my system today, color me a winner!

:mrgreen:

---

### Post by renatosilva on 2007-01-11
> **bodhi.zazen said:**
> Swap should be RAM X 2 ; 1 Gb max

The more ram you have, the less swap you need ...

I disagree. I have 1GB and don't use nothing special that would overhead it. So I don't need swap most of the time. Unless it's activated and frequently used even if RAM is free. Is it? 

A teacher told me about half of RAM as a good percent for swap. And remeber, in some emergency you can turn on more swap using a swap file in the fileystem.

I have 1GB, I guess I'll create 1GB swap instead of 512MB  just previewing future RAM upgrades to 2G or 4G...

---

### Post by bodhi.zazen on 2007-01-11
It depends somewhat on what applications you run.

When in doubt, I make a conservative recommendation.

_Here are some links you may find of interest_:

[http://www.linux.com/guides/sag/swap-allocation.shtml](http://www.linux.com/guides/sag/swap-allocation.shtml)

[http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html](http://www-128.ibm.com/developerworks/aix/library/au-satswapspace.html)

_Add a swap file_:

[http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3](http://www.ubuntuforums.org/showpost.php?&p=489196&postcount=3)
		[http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html](http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html)

_Memory management_:

[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?)

---

### Post by marx2k on 2007-01-11
> **dabl said:**
> 
On the other hand, even though I have 4GB of memory installed, everything I can find, including watching my system's statistics, indicates I wasted 2GB in that 4GB swap partition, so if I were doing it over, I would make it only 2GB for swap.

Resizing using gparted liveCD is always an option

---

