---
title: "Managing swap partition for Hibernation"
date: 2013-09-27
forum: General Help
---

### Post by sharathcshekhar on 2013-09-27
Hi All,
I have a Dell XPS Ultrabook with a Hybrid Drive/32G of SSD. I have installed my root partition and swap on the SSD and /home on my HDD. I have 8G of Ram and had allocated only 4G of swap on the SSD. Now I want to hibernate my laptop and need more swap. Is there any way I can create a 8G swap on my HDD to be used only for hibernation and continue using the partition on SSD for swapping (I am hoping creating a swap partition on SSD might give me some performance benefits). I do not want to waste 8G of SSD for swap. I have a very bulky installation with too many softwares taking about 25G of space for /. 
I am aware of the swap file option and understand it is not a very good choice for hibernation. Can some one please share the swap partition management strategy? Thanks in advance.


/* Ubuntu 13.04 system with classic Gnome */
Regards,
Sharath

---

### Post by DuckHook on 2013-09-27
> **sharathcshekhar said:**
> ...Is there any way I can create a 8G swap on my HDD to be used only for hibernation and continue using the partition on SSD for swapping...The short answer is: no. Moreover, it is not a good idea to use an SSD for swap anyway, as any I/O-intensive task will burn up your limited write cycles on the SSD. And with 8GB of DRAM you are probably not swapping too frequently anyway, so you shouldn't see much of a performance hit from basing swap out of the HDD. Last but not least, you may wish to set up separate HDD partitions for /var and /tmp as well. These directories generate lots of I/O for logs and temporary files, none of which need an SSD, but all of which diminish its useful life. However, it's harder to change the locations of these two directories without re-installing.

It is not hard to change a swap partition from your SSD to your HDD. The general idea would be to create some partition on your HDD that is larger than 8GB (if you want to hibernate, you must be careful to make it more than big enough due to the difference between GB and GiB), point your swap to the new partition by changing the UUID in fstab, make sure everything works (esp hibernate) and then delete your old SSD swap partition once everything is working. The instructions for creating/resizing swap partitions, etc. are [here]("https://help.ubuntu.com/community/SwapFaq").

There is less risk in dealing with swap than just about any other partitioning task because your system will continue to operate without a swap quite well. That said, be careful when you use gparted or any partitioning app, because a misplaced stroke could hose any of your more critical partitions.

---

### Post by Impavidus on 2013-09-27
Do you actually use your swap for swapping? 8GiB is such an amount of ram that you rarely need swap. I only use swap when discovering a memory leak and even then I don't really need it.

I thing it's quiet easy to move /var to your HDD. Use a live disk for that, copy all files from /var to the new partition and edit /etc/fstab. I think it can be done with /tmp too, but I'm not sure. /tmp might be needed too early in the boot process.

---

### Post by oldfred on 2013-09-27
If booting from SSD and you put hibernation on hard drive you may not boot much faster or even slower from hibernation. Normally Ubuntu boots pretty fast anyway and from SSD very fast.

---

### Post by sharathcshekhar on 2013-09-28
Thanks all the quick answers. Wearing out SSD due to many IOs of /tmp, /var and swap was something that had not occured to me. I think moving th swap to HDD would be my best option. Also, I recently upgraded my RAM form 4G to 8G. I have occasionaly seen swap being utilized when I was on 4G. But I think you are right about (almost) never using swap when running on 8G of RAM.
I would probably need hibernation not just for fast boot ups, but to restore my laptop to where I left. 
Thanks again for your answers, I really appreciate it. Marking the thread as solved.

Regards,
Sharath

---

### Post by oldfred on 2013-09-28
there is a difference between sleep mode and hibernation.
Sleep mode keeps power to RAM and hibernate copies RAM into swap and shutsdown.

---

### Post by sharathcshekhar on 2013-10-01
It sure is. But feels nice to hibernate at the end of your work at the university, go home come back and resume where you left. Suspending/sleeping might consume some battery.

---

