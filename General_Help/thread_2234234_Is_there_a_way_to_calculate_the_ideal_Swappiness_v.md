---
title: "Is there a way to calculate the ideal Swappiness value?"
date: 2014-07-13
forum: General Help
---

### Post by Al1000 on 2014-07-13
Packard Bell EasyNote E6307 laptop
1.8GHz AMD Sempron 3000+ CPU
768MB RAM
1GB swap partition
Kubuntu 12.04.4 LTS

I have been reading a lot of conflicting advice on changing the swappiness value, for example:

[http://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20](http://askubuntu.com/questions/184217/why-most-people-recommend-to-reduce-swappiness-to-10-20)

[URL="https://sites.google.com/site/easylinuxtipsproject/mint-mate-first#TOC-Decrease-the-swap-use-important-"]https://sites.google.com/site/easylinuxtipsproject/mint-mate-first#TOC-Decrease-the-swap-use-important-
[/URL]

Using:

```
cat /proc/sys/vm/swappiness
```

... to check the swappiness value, and:

```
sudo pico /etc/sysctl.conf
```

...to edit sysctl.conf, I added:

```
# Decrease swap usage to a reasonable level 
vm.swappiness=15 
# Improve cache management 
vm.vfs_cache_pressure=50
```

...to the file.

(I have no idea how the ''improve cache management'' script works, but thought I would put it in anyway as it was recommended in one of the links I posted - I'll maybe try commenting it out for a while to see if I notice any difference)

The result was, which I assume was due to decreasing swappiness from the default value of 60 to 15, that when the computer came to use the swap partition it froze for several seconds, and Shockwave Flash player crashed in Chromium browser which displayed a message saying the computer didn't have enough free RAM to be able to detect the problem and send a report to the developers.

I have now changed the value to 25 and it's working much better, although it's hard to tell if it's any better than it was with the value at 60.

As far as I understand it, the danger with reducing the value by too much, is that the computer might not have enough free RAM to run applications while it's writing to the swap partition, which I guess is what happened when I set the value to 15. Since the same application will use the same amount of RAM regardless of how much physical RAM there is, I assume the ideal swappiness value will be different for different computer. So I am wondering, is there a way to calculate what it should ideally be?

Most people offering advice seem to suggest changing the value to 10,  but I wonder how many are talking from experience with using a computer  that uses swap on a regular basis. 10 sounded radically low to me, which is why I started by changing it to a more conservative 15, but even that seemed to be too low as well. I wouldn't bother changing the value on my other computer that runs Kubuntu 14.04 as it has 3GB of RAM and never uses swap anyway, but as this old laptop uses swap most of the time with Kubuntu 12.04, it would seem to make sense to get it to use it as efficiently as possible.

---

### Post by philinux on 2014-07-13
Swappiness as i've just discovered is more like voodoo, experimentation maybe the best way to go.

---

### Post by tgalati4 on 2014-07-13
768 MB of RAM is shy by today's standards.  1 GB, 1.5 GB, or 2 GB is better for running Ubuntu.  You really want to avoid swap, since it just slows your system down.  Swapiness just changes how actively your system sends pages to swap to free up RAM.  Depending on how you use your computer (what apps are open) swapiness will either help or hurt.  Since your system is low on RAM, increasing swapiness might help because that frees up RAM for your active applications--but using that swap will cause some operations to slow way down, like opening up a new application or changing workspaces frequently.

As philinux suggests, you need to experiment to see what works.  The default values work in most cases, so don't be surprised if performance degrades going either way.

Post a summary of your experiences with swapiness versus hands-on performance.

---

### Post by grumblebum2 on 2014-07-13
When you first login how much ram is being used?
With your amount of ram I would only be running a lightweight DE like LXDE.

---

### Post by Al1000 on 2014-07-14
> **philinux said:**
> Swappiness as i've just discovered is more like voodoo, experimentation maybe the best way to go.

That sounds like good advice. Having tried setting the value to 15, I would guess that 10 would result in more of the same problems, so I don't understand why so many people advise setting the value to 10. Particularly in a list of ''things to do after installing an OS,'' this advice could result in people getting worse performance than they would otherwise have got had they left it alone.

---

### Post by Al1000 on 2014-07-14
> **tgalati4 said:**
> 768 MB of RAM is shy by today's standards.  1 GB, 1.5 GB, or 2 GB is better for running Ubuntu.  You really want to avoid swap, since it just slows your system down.  Swapiness just changes how actively your system sends pages to swap to free up RAM.  Depending on how you use your computer (what apps are open) swapiness will either help or hurt.  Since your system is low on RAM, increasing swapiness might help because that frees up RAM for your active applications--but using that swap will cause some operations to slow way down, like opening up a new application or changing workspaces frequently.

As philinux suggests, you need to experiment to see what works.  The default values work in most cases, so don't be surprised if performance degrades going either way.

In what cases does the default value of 60 not work?

I don't follow how just because the default value works, that would necessarily be the best value.

> 
Post a summary of your experiences with swapiness versus hands-on performance.

You mean like I did in the OP?

To update what I posted in the OP, I haven't changed the value from 25, and would guess that performance may be slightly better than it was at 60.

---

### Post by Al1000 on 2014-07-14
> **grumblebum2 said:**
> When you first login how much ram is being used?

271MB with Conky running.

[IMG]http://i1175.photobucket.com/albums/r622/AL0001/snapshotKubuntu5_zpsf0f7ead5.jpeg[/IMG]

Is there a way to use that figure to calculate what swappiness should ideally be on this computer?

> 
With your amount of ram I would only be running a lightweight DE like LXDE.

Because this is an old laptop, the graphics aren't up to running many of the modern distros. I have been advised that Xubuntu 12.04 might work, so may give that a shot at some point to see what it's like. I haven't tried Lubuntu 12.04, but I briefly tried Lubuntu 14.04 on my other computer, and reckon I would rather stick with Kubuntu 12.04 on this laptop rather than use Lubuntu 12.04 even if it does work.

I use Lucid Puppy 5.2.8.6 for most resource intensive applications on this laptop anyway, and it only uses around 80MB of RAM after booting up. I've seen it use up to 850MB of the swap partition while downloading several videos at once, but even that only used around 60% of CPU resources so the computer was still usable.

---

### Post by buzzingrobot on 2014-07-14
The thing about avoiding use of swap is that when your system needs to use swap, and can't find it,  your system will probably crawl to a halt because it's run out of RAM.  Swap is there to temporarily substitute for RAM.

The reason using swap makes things slower is that the kernel is substituting hard drive space for space in RAM.  That happens when a program or process makes a request for RAM that cannot be fulfilled.  I.e., when all available RAM is already allocated and in use. 

So, rather than grind to a halt at that moment, the kernel copies a chunk of memory from RAM out to the drive, thereby freeing up a bit of memory.  When the memory that's stored on the drive is needed, the kenel moves it back into RAM, swapping out another chunk if necessary.

Since hard drives are many orders of magnitude slower than memory chips, things do get pretty slow when swap is in use. But, that's better than the alternative.

Machines with marginal RAM are precisely the machines that are going to need to use swap frequently.

I don't play with "swappiness" so I can't offer any suggestions about that.  But, if I had the OP's machine, I'd just leave it alone.  You can't fit two liters of water in a one-liter bottle.             

Memory use varies, but it isn't unusual to see an OS plus a desktop environment consume 500-600 megs of RAM all by themselves. That's the majority of a 768 meg RAM capacity.  Open a browser and another app and you're either swapping or on the verge. Here, for example, Firefox with no added extensions and the default plugins  takes 150-170 megs after launch,  If I add Adblock Plus, for comparison, Firefox will jump to 350-400 megs or more. (Ad blockers require lots of memory.)

---

### Post by tgalati4 on 2014-07-14
Setting swapiness to 10 is almost equivalent to "Don't use swap, period."  So your system will essentially freeze when you run out of memory--and that is an indication that you can't do what you want to do on your system.  In that case, you will need to get more RAM.

The default settings allow the system to fail gracefully.  It is subtle; you don't notice it at first, then everything just crawls.  When you set it to 10, it's like a hammer hitting you on the head.  Without swap, the kernel will unceremoniously kill processes (and any work that you haven't saved).

There is no ideal setting, it just gives you the illusion of control.  Some people like that.

---

### Post by Al1000 on 2014-07-15
> **tgalati4 said:**
> Setting swapiness to 10 is almost equivalent to "Don't use swap, period."  So your system will essentially freeze when you run out of memory--and that is an indication that you can't do what you want to do on your system.  In that case, you will need to get more RAM.

The default settings allow the system to fail gracefully.  It is subtle; you don't notice it at first, then everything just crawls.  When you set it to 10, it's like a hammer hitting you on the head.  Without swap, the kernel will unceremoniously kill processes (and any work that you haven't saved).

There is no ideal setting, it just gives you the illusion of control.  Some people like that.


We have established that some settings work better than others, and discussed reasons as to why. The one that works best of all, would be the ''ideal setting.''

As philinux suggested, experimentation may be the way to go. So far I have discovered that 15 is too low, but have not had any problems with it at 25. As it would use less swap with the value at 25 than at 60, the former is surely better than the latter.

While trying to find the absolute ideal setting through experimentation would probably be more trouble than it's worth, it does seem prudent to get it into the best ballpark.

---

### Post by tgalati4 on 2014-07-15
But your workflow changes frequently.  If you watch youtube videos, some may be short, others may be long, you may have 10 tabs open, you may have 25 tabs open.  Each case uses a different amount of RAM, so setting swapiness to a "best" value may be difficult.

If you are writing a 400-page book in LibreOffice, then perhaps you can find a balance with swapiness that reduces the "draggy mouse" or slow page loading that happens when you are low on RAM.  For this single use case, you may be able to find a "best" swapiness value.  With a changing workload, I don't think there is a best value.

---

### Post by ibjsb4 on 2014-07-15
swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible 

This seems to work for me, but I have 4G of ram.

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by Al1000 on 2014-07-15
> **tgalati4 said:**
> But your workflow changes frequently.  If you watch youtube videos, some may be short, others may be long, you may have 10 tabs open, you may have 25 tabs open.  Each case uses a different amount of RAM, so setting swapiness to a "best" value may be difficult.

If you are writing a 400-page book in LibreOffice, then perhaps you can find a balance with swapiness that reduces the "draggy mouse" or slow page loading that happens when you are low on RAM.  For this single use case, you may be able to find a "best" swapiness value.  With a changing workload, I don't think there is a best value.

My 'workflow' doesn't really change much on Kubuntu on this laptop at all. But even if it did, there would still be a value that would be best overall, even if it was the default value.

As I mentioned earlier I boot into Puppy for resource intensive applications, which includes watching long videos, and I do all of my office work on my desktop pc.

---

### Post by Al1000 on 2014-07-15
> **ibjsb4 said:**
> swappiness=0 tells the kernel to avoid swapping processes out of physical memory for as long as possible 

This seems to work for me, but I have 4G of ram.

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

Why did you bother to change the value, if the computer has 4GB of RAM?

I couldn't see the point in changing the value on my other computer which has 3GB of RAM, as I've never seen it use swap.

---

### Post by ibjsb4 on 2014-07-15
> **Al1000 said:**
> Why did you bother to change the value, if the computer has 4GB of RAM?

I couldn't see the point in changing the value on my other computer which has 3GB of RAM, as I've never seen it use swap.

With standard settings I have gone to swap on occasion.

---

