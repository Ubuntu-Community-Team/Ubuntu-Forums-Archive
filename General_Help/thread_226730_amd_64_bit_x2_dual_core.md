---
title: "amd 64 bit x2 dual core"
date: 2006-07-31
forum: General Help
---

### Post by william_nbg on 2006-07-31
I have a chance to pick-up a amd x2 939 pin quite cheap from a friend, and it should run fine on my mainboard which is a 939 pin asus.

My question is: would I have to do a fresh install or could I just pop the sucker in and reboot??

Second question: to use the K7-smp kernel would I have to run in 64 bit, or could I run it also in 32 bit??

---

### Post by jamesford on 2006-07-31
not sure about reinstalling but the k8 kernel if u run 64 bit ubuntu or k7-smp if u go 32 bit will be fine, ive ran both without any probs

---

### Post by william_nbg on 2006-07-31
> **jamesford said:**
> not sure about reinstalling but the k8 kernel if u run 64 bit ubuntu or k7-smp if u go 32 bit will be fine, ive ran both without any probs

Thanks for the reply. I'll ask around about the reinstall. Is there a big performane increase from the 64 bit to the 64 bit x2??

---

### Post by Ronbo on 2006-07-31
I am running an AMD X2, upgraded from an Athlon 64.  I run it in 32 bit with this kernel:

linux-image-2.6.15-26-K7

It's the Linux kernel image for version 2.6.15 on AMD K7 SMP/UP

If your already runniny in 32 bit and want to run the K7 kernel in 32 bit you can just install this kernel via Synaptic and reboot into it.  When it reboots go to System->Adminmistration->System Monitor and it should list CPU 1 and CPU 2 under CPU history.  I didn't have to do a reinstall and everything works the same, just faster.  As far as running in 64 bit I don't do it because there are less packages than in 32 bit, some pretty popular ones are missing in 64 bit too.  Plus from what I've read from posts on this forum there isn't much, if any, of a speed difference from 32 bit to 64 bit.

---

### Post by william_nbg on 2006-07-31
> **Ronbo said:**
> I am running an AMD X2, upgraded from an Athlon 64.  I run it in 32 bit with this kernel:

linux-image-2.6.15-26-K7

It's the Linux kernel image for version 2.6.15 on AMD K7 SMP/UP

If your already runniny in 32 bit and want to run the K7 kernel in 32 bit you can just install this kernel via Synaptic and reboot into it.  When it reboots go to System->Adminmistration->System Monitor and it should list CPU 1 and CPU 2 under CPU history.  I didn't have to do a reinstall and everything works the same, just faster.  As far as running in 64 bit I don't do it because there are less packages than in 32 bit, some pretty popular ones are missing in 64 bit too.  Plus from what I've read from posts on this forum there isn't much, if any, of a speed difference from 32 bit to 64 bit.

Thanks for the info!

I'm already running the k7 kernel, though, wouldn't I want the k7-smp kernel if I switched the cpu to a dual core??

---

### Post by Ronbo on 2006-07-31
If you run System Monitor in CPU History how many CPU's does it show?

---

### Post by Ronbo on 2006-07-31
Check out this post:

[http://www.ubuntuforums.org/showthread.php?t=193551&highlight=k7+smp](http://www.ubuntuforums.org/showthread.php?t=193551&highlight=k7+smp)

I knew I saw it somewhere on the forums, SMP support is now built into the K7 and 686 kernel, so there is no need for a linux-K7-SMP.  You had me wondering, I even checked my own system monitor and saw that it was utilizing both cores.

---

### Post by william_nbg on 2006-08-01
Cool. I didn't know that. I thought I had to put the smp kernel in to get hyper threading. Like I said earlier, I'm running an amd 64b 3200 now, but a friend offered me an amd 64b 4000 x2 for about 100 eu (I'm hoping).

When you upgrading to the x2 did you notice a big performance jump??

---

### Post by william_nbg on 2006-08-01
Cool. I didn't know that. I thought I had to put the smp kernel in to get hyper threading. Like I said earlier, I'm running an amd 64b 3200 now, but a friend offered me an amd 64b 4000 x2 for about 100 eu (I'm hoping).

My biggest worry was that I'd have to do a fresh install after changing the cpu, because I don't have a lot of time these days, it would take me 3 days to set up everything the was I  have it now.:^o 

When you upgrading to the x2 did you notice a big performance jump??

---

### Post by Ronbo on 2006-08-01
I did notice a perormance jump, but I also upgraded the memory from 256 Megs to 1 Gig.  So I am not sure how much of the performance increase is attributed to the processor upgrade and how much to the memory upgrade. Let me know how you make out and what type of an increase in peformance you notice.  I'd be curious to see if the upgrade in the memory makes that much of a difference.

---

### Post by william_nbg on 2006-08-02
> **Ronbo said:**
> I did notice a perormance jump, but I also upgraded the memory from 256 Megs to 1 Gig.  So I am not sure how much of the performance increase is attributed to the processor upgrade and how much to the memory upgrade. Let me know how you make out and what type of an increase in peformance you notice.  I'd be curious to see if the upgrade in the memory makes that much of a difference.


OK, I'll let you know, but it'll be at least a week before I can get the cpu and pop it in. I already have plenty of ram, so I'll just change the cpu.

William

---

### Post by william_nbg on 2006-08-12
Got it, and installed it this weekend. 

I notice a nice difference. Ok, I went from a 3.2 to 3.8 as well.

I had to update my bios before it recognized my new cpu, though now it's working great.

---

