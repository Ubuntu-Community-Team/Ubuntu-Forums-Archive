---
title: "Challenge for savvy users: boot and start-up my system in less than 15 seconds!"
date: 2008-06-21
forum: General Help
---

### Post by the8thstar on 2008-06-21
Hello all,

I have a challenge for the most savvy users out there. Currently my system (spec in sig below) takes about 50 seconds to load completely (Grub countdown not included).

**[COLOR="Blue"]_The whole idea is to bring it down to only 15 SECONDS_[/COLOR]**. I'm willing to share the contents of my boot files on the forum to help tweak my system. I'm also willing to try several options to get the best result.

If you know your trick makes the system unstable, please do not share it. I only want durable solutions, not a quick fix that is going to crash the computer down the road.

Feel free to ask any questions to better understand my config. 

Ultimately, I'd like other users to benefit from our exchange.

Ok, so what's YOUR trick?

---

### Post by inportb on 2008-06-21
Booting the system once with the "profile" kernel parameter speeds up subsequent boots. Perform whenever kernel or modules are changed.

Hm, I'm interested in these techniques too. *subscribes*

---

### Post by sdennie on 2008-06-21
Also have a look at this thread: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

---

### Post by the8thstar on 2008-06-21
I wanted to post my results for BootChart, but I don't know how to run it. Initramfs perhaps?

---

### Post by dicecca112 on 2008-06-21
> **the8thstar said:**
> I wanted to post my results for BootChart, but I don't know how to run it. Initramfs perhaps?

install bootchart and reboot.  There will be an image in var/log/bootchart

And the only way you are going to get sub-30 second boot is with an SSD

---

### Post by the8thstar on 2008-06-21
> **dicecca112 said:**
> install bootchart and reboot.  There will be an image in var/log/bootchart

And the only way you are going to get sub-30 second boot is with an SSD

Thanks. What is an SSD?

---

### Post by LordKelvan on 2008-06-21
I believe SSD stands for Solid-State Drive.  The difference between it and normal hard drives is that SSD's are flash-based, and as such have no moving parts.  

Advantages: Read accesses are very fast, read/write latencies are low, low noise, less power

Disadvantages: Write accesses are generally slower, **extremely expensive (when compared to normal hard drives)** and limited number of writes (i.e., you can only write to each cell of an SSD a limited number of times).

For many people, I think the biggest issue would be the price :D (although I don't have numbers off the top of my head - perhaps someone else does)

Cheers,
LK

---

### Post by mvaniersel on 2008-06-21
Interesting idea. I've never managed to shave off more than a few minutes using prelinking, profiling and other voodoo. But I'm curious what can be achieved if the community takes a look at your bootchart.

---

### Post by dicecca112 on 2008-06-21
> Disadvantages: Write accesses are generally slower, **extremely expensive (when compared to normal hard drives)** and limited number of writes (i.e., you can only write to each cell of an SSD a limited number of times).



The lifetimes of SSDs are longer than conventional HDDS, and the write speeds are only slower on the cheap ones. There is an algorithm that determines where to write, in order to achieve the longest lifetime.  You would  have to right 50GB per day and even at that your HDD would last for 35years (of course this depends on the size, smaller the shorter the lifetime, but this is the average for 30-64GB SSDs)  Even the moderately priced ones (well moderately in terms of SSDs) have at least 60MB/s writes, which are competitive with most HDDs, just not the High speed Raptors

---

### Post by RedSquirrel on 2008-06-21
[http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/](http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/)

---

### Post by the8thstar on 2008-06-21
Okay, here is my latest Bootchart (see attachment). I hope this will help!

---

### Post by the8thstar on 2008-06-22
Bump

---

