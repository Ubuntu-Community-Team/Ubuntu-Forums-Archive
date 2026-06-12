---
title: "redirect cache to SSD swap"
date: 2012-12-23
forum: General Help
---

### Post by smo0th on 2012-12-23
hi, I'm planning to use a SSD(a cache drive) for swap purposes, storing the cache in a swap partition inside the SSD, but I cannot find any means of specifically redirecting the cache to swap, is there any way to do this?

---

### Post by Pjotr123 on 2012-12-23
I'm not sure what you aim to achieve by this.... An SSD is unfit for intensive swap usage. Maybe you'll find this complete how-to for SSD's useful:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Good luck! :)

---

### Post by smo0th on 2012-12-23
thanks Pjotr123, it might be best to just set the SSD partition as swap and forget about everything else, but just for the fun of it, I would like to say to the OS to use the SSD partition for cache, so the RAM has more space for the applicacions and system data, I know this is a weird one but I would like to do some testing and see if it helps somehow, thanks for the link I find it very useful, I already followed some of the advices here: [http://vasilisc.com/speedup_ubuntu_eng](http://vasilisc.com/speedup_ubuntu_eng) they are also helpful :)

---

### Post by Cheesemill on 2012-12-24
> **smo0th said:**
> it might be best to just set the SSD partition as swap and forget about everything else, but just for the fun of it, I would like to say to the OS to use the SSD partition for cache, so the RAM has more space for the applicacions and system data

This 'cache' that you are talking about ***is*** swap. There is nothing more you can do than setting up swap on your SSD.

---

### Post by Pjotr123 on 2012-12-24
As Cheesemill says. You might *increase* the swappiness, but that's rather perverse for an SSD, as it'll kill it long before it's normal life span has ended. And it probably even won't make your system any faster....

Increasing the RAM amount makes much more sense. And it's quite safe.

About acceleration tips in general: you nearly always pay a price. In reduced features, in worse looks or even in reduced stability or shortened life span. You should realize that.

If you're smart, you'll only consider safe tweaks that will "merely" reduce features or looks. Speed increase at the price of reduced stability or shortened life span is "fools' gold".

For your information: I've collected a couple of safe tweaks to increase speed: [https://sites.google.com/site/easylinuxtipsproject/speed](https://sites.google.com/site/easylinuxtipsproject/speed)

---

### Post by smo0th on 2012-12-24
thanks Pjotr123, your answer is quite reasonable, so far I have only done safe tweaks :)

hi Cheesemill, sorry I didn'tmake clear enough, by cache I mean the memory portion allocated in RAM which is just that, if you use htop, there are 3 colors for the RAM, green is the one used by processes, blue is the one used for buffers and yellow is the one for cache, I have noticed that when the green and blue grow, the yellow just dissapears not being allocated in swap, this is why I would like to send all the cache to swap, as far as I know swap is a copy of what runs in the RAM, so eventually the cache being used would be transfered to RAM and run from there, read/write access time  is far faster in a SSD than in a spinning mechanism, so I think that could help somehow in the overall performance :)

---

### Post by rnerwein on 2012-12-24
> **smo0th said:**
> hi, I'm planning to use a SSD(a cache drive) for swap purposes, storing the cache in a swap partition inside the SSD, but I cannot find any means of specifically redirecting the cache to swap, is there any way to do this?
hi
no good idea. this will slow down your box extreamly. but you can write a little shell script which runs - lets say all 10 minutes with following contens.

  sync
#       echo 3 > /proc/sys/vm/drop_caches
#       1 --> free pagecaches, 2 --> free dentries and inodes,3 --> free all

cheers

---

### Post by smo0th on 2012-12-24
thanks rnerwein, that is indeed a good advice, thank you all for your answers on this thread, merry christmas!! :D

---

### Post by dcstar on 2012-12-24
> **smo0th said:**
> 
hi Cheesemill, sorry I didn'tmake clear enough, by cache I mean the memory portion allocated in RAM which is just that, if you use htop, there are 3 colors for the RAM, green is the one used by processes, blue is the one used for buffers and yellow is the one for cache, I have noticed that when the green and blue grow, the yellow just dissapears not being allocated in swap, this is why I would like to send all the cache to swap, as far as I know swap is a copy of what runs in the RAM, so eventually the cache being used would be transfered to RAM and run from there, read/write access time  is far faster in a SSD than in a spinning mechanism, so I think that could help somehow in the overall performance :)

Why do people continually believe that they can manage system resources better than people who been specialising in this area for decades?

The "cache" exists to utilise RAM that would otherwise be wasted doing nothing by speculatively retaining disk sectors *in case* they might be needed again, as other more important system components require RAM it is reallocated and disk data that may have been cached has to be transferred directly from the (slower) disk storage.

It is pointless - and basically stupid - to dump cached disk blocks that may never be used to swap (or anywhere). Swap exists to store data that *must* exist in VM and is deemed more efficient to be in that location rather than main RAM.

---

### Post by smo0th on 2012-12-24
thanks David, that was a real good explanation on this subject, I understand your feelings about hordes of people thinking that they can do better, I fully and deeply respect linux contributors since Torvalds, this thread gives me a better picture of what I googled so far and this is why I love this forums, now I know what to do with my SSD, definitely not the idea I had :) thanks!

---

### Post by rnerwein on 2012-12-25
> **dcstar said:**
> Why do people continually believe that they can manage system resources better than people who been specialising in this area for decades?

The "cache" exists to utilise RAM that would otherwise be wasted doing nothing by speculatively retaining disk sectors *in case* they might be needed again, as other more important system components require RAM it is reallocated and disk data that may have been cached has to be transferred directly from the (slower) disk storage.

It is pointless - and basically stupid - to dump cached disk blocks that may never be used to swap (or anywhere). Swap exists to store data that *must* exist in VM and is deemed more efficient to be in that location rather than main RAM.
hi
the enhancement is "must exist" that's true. data goes to swap if the system need i to put it there.
just a little example: you read/write a very huge file (it does't matter how memory you got - just read/write a bigger file) then the cache is filled up with may be never used
data. why not flush the cache from time to time ( i know the system will do it too) before the system starts swaping with althoug usless data ?
cheers

---

### Post by Cheesemill on 2012-12-25
> **smo0th said:**
> hi Cheesemill, sorry I didn'tmake clear enough, by cache I mean the memory portion allocated in RAM which is just that, if you use htop, there are 3 colors for the RAM, green is the one used by processes, blue is the one used for buffers and yellow is the one for cache, I have noticed that when the green and blue grow, the yellow just dissapears not being allocated in swap, this is why I would like to send all the cache to swap, as far as I know swap is a copy of what runs in the RAM, so eventually the cache being used would be transfered to RAM and run from there, read/write access time  is far faster in a SSD than in a spinning mechanism, so I think that could help somehow in the overall performance :)
You've got to take a step back and think about what's being cached. The only things that are cached are recently used program files and documents. If you have your root and home directories on the SSD anyway like you should if you are using one then you would gain no performance benefits from offloading your cache to the SSD as this is where the documents/programs already live, you'd just have 2 copies of exactly the same data on the SSD.

While we are talking about cache, one way that you can get a perceived performance increase from your system is to use preload. Preload keeps track of your most used programs and documents and preloads them into the cache when the system is booted. This way when you use a program for the first time it is already loaded into memory so it will start a lot quicker.

---

