---
title: "Swap Size"
date: 2014-11-18
forum: General Help
---

### Post by box02-0 on 2014-11-18
Hi.

I am upgrading my Computer and will be going to Ubuntu 14.04 from 12.10. The new system will have twin 256gb SSD's and 16gb of RAM.

Normally, I would make the Swap size equal to the RAM size, in my case 16gb. Does this apply for SSD drives as well? Am I better off to use more Swap size than 16gb? I don't game. or do high end graphics. I will be using hernate.

Thanks,

M...

---

### Post by Pilot6 on 2014-11-18
You do not need swap for a system with 16GB of RAM, unless you want to use hibernate.

---

### Post by ajgreeny on 2014-11-18
With an ssd a cold boot will be fast enough that you won't really ever need to hibernate, I would think

---

### Post by ibjsb4 on 2014-11-18
> **ajgreeny said:**
> With an ssd a cold boot will be fast enough that you won't really ever need to hibernate, I would think
Yep, why use it.

---

### Post by box02-0 on 2014-11-19
The only reason I can think of using hibernate is if you were in the middle of a "bunch" of things and had to quit, but wanted to come back exactly where you were. Not something I would worry about, so I think I will try the system without swap as per your advice.

Thank you all for you advice.

M...

---

### Post by pfeiffep on 2014-11-19
I suggest a small swap size 1 or 2 GB just in case your application(s) run out of memory - that way you won't loose your work!

---

### Post by buzzingrobot on 2014-11-19
Your system will want to swap, basically, when it's asked to put more into RAM than there is available RAM. The amount of RAM determines the threshold, which varies depending on what the machine is doing at any given moment. 

Whether you need swap, in an absolute sense, depends on your usage habits.  The OS expects it to be there.  If it needs to use swap and none exists, it will likely just freeze, or at least become seriously recalcitrant, until you manage to unload something.

I have a machine with 32 gigs of RAM and I can make it swap with the partition sized at 32 gigs.  

But, in the normal course of events, I set swap at 16 gigs on that machine.  It sees use occasionally when I load up a huge batch of huge photo files for editing.

---

### Post by ibjsb4 on 2014-11-19
You do not have to remove the swap partition to run without swap.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=turn+swap+off&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=turn+swap+off&sa=Search&cof=FORID:9)

Other considerations:
swappiness
vfs_cache_pressure
zram

[https://www.kernel.org/doc/Documentation/sysctl/vm.txt](https://www.kernel.org/doc/Documentation/sysctl/vm.txt)
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)
[https://blueprints.launchpad.net/lubuntu-brainstorming/+spec/zram-config](https://blueprints.launchpad.net/lubuntu-brainstorming/+spec/zram-config)

---

### Post by QIII on 2014-11-19
I do a lot of scientific computing on one of my machines with 16GB of RAM.  Since it's not a supercomputer, it very rarely uses more than about 4GB.  16GB is really overkill -- but we all like our toyz!  In most use cases, 16GB is wildly overboard.

I don't run with any swap partition at all on my desktops, since I don't hibernate.  On my laptop I go with 1.1 x RAM for swap so I can hibernate.

I would certainly avoid swapping to my SSDs if I ever needed it unless that were the only drive on the machine.  Swap to a spinner.

In these days of big RAM, swap is somewhat outmoded except for hibernation.

That said, I wouldn't bother fooling around with the swap partition at this point.  Deleting, moving or extending partitions can wreak havoc on assigned UUIDs. Unless you want to use blkid from the Live media to find your new UUIDs and modify your fstab -- or restart in recovery mode, use blkid to find your new UUIDs and then modify fstab with nano or something its just too much trouble.

Theoretically swap = RAM is sufficient to retain memory state.  I go with 10% over just because ...

---

### Post by box02-0 on 2014-11-20
".....I don't run with any swap partition at all on my desktops, since I don't hibernate.  On my laptop I go with 1.1 x RAM for swap so I can hibernate.
I would certainly avoid swapping to my SSDs if I ever needed it unless that were the only drive on the machine.  Swap to a spinner.
In these days of big RAM, swap is somewhat outmoded except for hibernation.
That said, I wouldn't bother fooling around with the swap partition at this point...."

Hi.

I'm a little confused with the last statement. I'm building this machine from scratch, so I can partition the SSD drives any way I want. I will be bringing in Ubuntu 14.04, and building the software up from scratch.

So the general consensus is no swap partition on the disk (I really don't want to add a spinner).

So, if no swap partition, what should I set swappiness to?

Thanks,

M...

---

### Post by QIII on 2014-11-20
Sorry.  I read that as you had already partitioned.
 
If you plan to hibernate, you need swap.

1.1 to 1.25 RAM is sufficient.  Reduce swappiness.

---

### Post by box02-0 on 2014-11-20
No Problem.
 In the current system I have swappiness set to 10. For the new guy, should I go for less than 10? I have seen a suggestion of swappiness=0. Does that make sense?

Thanks for your help,

M...

---

### Post by ibjsb4 on 2014-11-20
I also thought you had a swap partition.  Without a swap partition, swappiness does not apply.

When I do use a swap partition on something that has a lot of ram, I set it to =0.

---

### Post by box02-0 on 2014-11-20
Hi.

Okay, no swap partition on disk and no worries about swappiness. Great.

Leads me to 2 more questions:

Should I use ZRAM?

AND, this is a little tougher since it is based on the kind of things that I do on my system, but would 16gb of RAM generally be adequate, or should I go for 32gb? I don't game or play videos or do any heavy scientific callculations.
 But if I was to do internet research AND run libre office AND Jedit AND dosbox AND libreCAD all at once, would 16gb generally be adequate?

Thanks for all the info,

M...

---

### Post by ibjsb4 on 2014-11-20
> Should I use ZRAM?
I been asking myself the same question :)  I do not run a swap partition on my desktop, but 
there are processes that use swap as storage for old files.  And even though it has not been a problem to date, I wonder if having 500M of zram might not be a bad idea.  I'm thinking out loud.
> would 16gb generally be adequate?
I think more like overkill, but who am I to say.  Got 24G myself and always looking for ways to use more, I have not been able to use it up.  Just run it.  You will know if you run out, your system will crash.  But I say that highly unlikely.

---

### Post by Mike_Walsh on 2014-11-20
Hi, box02-0.

I'm pretty new at this game; but I noticed you said in reply to why you want to hibernate, "in case I'm in the middle of a bunch of things, and want to come back to it exactly as it was".

I'm surprised nobody's mentioned this; rather than mess about with hibernation, why not use 'suspend'? It's what I do in that particular situation; I often have two or three graphics apps on the go, at least one browser open with anything up to 10 tabs or so, maybe Skype, too....it works perfectly (at least in 14.04).

And you don't need to worry about 'swap', neither; since it's NOT saving and re-instating.....merely holding the data in RAM with very minimal voltage, until you want to resume what you were doing. It's faster on re-start than hibernation, too (at least, I find that to be the case; but then, I only have 3 GB of RAM.....my mainboard won't take any more than 4 GB. Vintage XP-era, y'see....)

Regards,

Mike. ;)

---

### Post by ajgreeny on 2014-11-20
Suspend is fine for a desktop plugged in to a mains electricity supply, but for a laptop which is running on battery, there is a finite time that the battery will last, and if it goes out of power you are lost, as is all your open work.

I speak from experience as I have an old netbook whose battery lasts only about 1.5 hrs; when in suspend mode it takes very little power, I agree, but I have left it too long on occasion and lost any unsaved work when the battery ran out totally.  If it had been hibernated all would have been saved.

---

### Post by ibjsb4 on 2014-11-20
Hay ajgreeny

What do you think about zram?  Post #15, good idea or am I blowing smoke?

---

### Post by ajgreeny on 2014-11-21
> **ibjsb4 said:**
> Hay ajgreeny

What do you think about zram?  Post #15, good idea or am I blowing smoke?

I have no experience or useful knowledge of zram so can't really give you an answer to that.

---

### Post by Mike_Walsh on 2014-11-21
> **ajgreeny said:**
> Suspend is fine for a desktop plugged in to a mains electricity supply, but for a laptop which is running on battery, there is a finite time that the battery will last, and if it goes out of power you are lost, as is all your open work.

I speak from experience as I have an old netbook whose battery lasts only about 1.5 hrs; when in suspend mode it takes very little power, I agree, but I have left it too long on occasion and lost any unsaved work when the battery ran out totally.  If it had been hibernated all would have been saved.

Point taken, AJ! I've been using a desktop for years, and only occasionally use my old laptop. I tend to forget that for many people, the laptop is their main machine...

My old Inspiron lasts me about 3.5 hours on the battery. It's 11 years old, and I had to replace the battery 2 1/2 years ago. So I took the opportunity to replace the normal-spec pack with a high-capacity one; it was a good investment.

Regards,

Mike.

---

### Post by Bloodcage on 2014-11-22
Changing swappiness to a lower value only makes sense if you use server which is running the whole day and needs effectiveness but those servers normally have enough RAM installed. For the normal Desktop / netbook user, the setting of swappiness = 60 is the best especially if you have only 2 GB of ram. those who are running ubuntu on a system with more RAM won't benefit from it at all. I've read about 100 articles about this topic, tested different settings on different systems and it was NEVER a real perfomanceboost like they all promise in their articles with a swappiness value below 60 on the common desktop or netbook systems.

---

### Post by ibjsb4 on 2014-11-22
> **Bloodcage said:**
> Changing swappiness to a lower value only makes sense if you use server which is running the whole day and needs effectiveness but those servers normally have enough RAM installed. For the normal Desktop / netbook user, the setting of swappiness = 60 is the best especially if you have only 2 GB of ram. those who are running ubuntu on a system with more RAM won't benefit from it at all. I've read about 100 articles about this topic, tested different settings on different systems and it was NEVER a real perfomanceboost like they all promise in their articles with a swappiness value below 60 on the common desktop or netbook systems.
I do not think of swappiness as a performance booster.  Its a tweak that can be made to regulate when swap kicks in (and everything slows down).  Results will vary.  Different equipment yeilds different results.

My laptop has 4G of ram, 4G swap partition and swappiness=0.  Set at the default =60, swap at times would kick in even though I had free ram.  At current setting swap very rarely kicks in.

My desktop machine does not have a swap partition, but the virtual machines running on it have 2G ram; 500M swap partition and swappiness=60.  That works well on them, swap has never kicked in.
> swappiness can have a value of between 0 and 100

swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible

swappiness=100 tells the kernel to aggressively swap processes out of physical memory and move them to swap cache
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by Bloodcage on 2014-11-23
Yes, I can't remember how often I read this. If you prevent the possibility to swap out pages less RAM is left for applications. The kernel makes the decision to swap out or not even if the swappiness is set to 10 but the likelihood shrinks. The benefit differs with users behavior and which programs you're using in the end. The last thing you should do is to set a swappiness value of 10 if you have only 2gb of ram, you are using unity as default and you are a user who opens many programs such as firefox, gimp, rythmbox and so on at the same time. Maybe it is possible to raise the reaction time of these programs but surely not if you dramatically reduce the value to 10. This is something everyone has to test on ones system because it differs from user to user and system to system. The default of 60 is a good default. I've tested from 0 to 100 over a long time and the final values were 40 on my 2gb netbook and 60 on my 4gb quadcore desktop system. 
There are so many discussion on that topic so everybody has to try for themselves.

---

### Post by buzzingrobot on 2014-11-23
> **Bloodcage said:**
> Changing swappiness to a lower value only makes sense if you use server which is running the whole day and needs effectiveness but those servers normally have enough RAM installed. For the normal Desktop / netbook user, the setting of swappiness = 60 is the best especially if you have only 2 GB of ram. those who are running ubuntu on a system with more RAM won't benefit from it at all. I've read about 100 articles about this topic, tested different settings on different systems and it was NEVER a real perfomanceboost like they all promise in their articles with a swappiness value below 60 on the common desktop or netbook systems.

I've never messed with swappiness and don't see the point. Swap exists for a reason. When you need it, you need it. Of course, operations will slow down, because physical memory is being used to temporarily supplement what is an inadequate amount of RAM. The alternative is worse:  No operations. (It's not a matter of all of RAM being written out to a drive, as some have said.) 

The best fix is more RAM.

---

### Post by Bloodcage on 2014-11-23
Exactly. More RAM or just use a lighter desktopmanager like LXDE or openbox and shut down some processes you don't need. Install preload and this is far more effective than messing with swappiness.

---

