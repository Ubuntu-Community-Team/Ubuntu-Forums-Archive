---
title: "Benefits of extra memory"
date: 2018-11-03
forum: General Help
---

### Post by mcsheffrey on 2018-11-03
I'm currently running ubuntu 18.10 on a dell laptop with 8 GB of RAM, using on average 5GB. What are the benefits of adding an additional 8GB. would this be used for extra cashing or anything else to speed up things.  Roy

---

### Post by Mark Phelps on 2018-11-03
I have experimented with my own desktop with memory sizes of 8GB, 12GB and 16GB -- and have failed to see ANY performance gain from the memory in excess of 8GB.

Perhaps others using more memory-intensive apps can weight in on this, but my advice would be NOT to waste the money on additional memory.

---

### Post by Autodave on 2018-11-03
Unless you are running a VM (virtual machine), you will not get any better performance with more memory.  Better to spend your money and get an SSD if you don't have one already.  Get a small one (120G for about $35 US) and use your spinning drive for storage of pics, videos, music, etc.

---

### Post by HermanAB on 2018-11-04
More than 8GB RAM is only needed for virtual machines, video editing, or complex engineering calculations/simulations with millions of variables.  I have on occasion wished I had a 24 core machine with 256 GB RAM, but then I divided the problem into a few smaller parts and found a way to make do.

---

### Post by mcsheffrey on 2018-11-04
But it looks like there is some benefits to having more than the 5GB its using for processes. In "top" it shows it using an extra GB, I'm assuming for caching.  Tks Roy

---

### Post by Autodave on 2018-11-04
Unless you are using every bit of that 8 gig of RAM, you will not gain a thing by adding more RAM.  There are several programs that you can get to show what load the memory is on. *System Load Monitor* is a good one.  You should be able to add it to the menu bar and keep tabs on your RAM usage continually.

Linux is not Windows: please try to keep your per-conceived ideas about Windows separate from Linux.  The machine that I am on right now is a dual boot with Win 10 and Xubuntu 18.04.  Win 10 uses about 6 times the amount of RAM that Xubuntu uses: just booting up and sitting there doing nothing.  (And on top of that, the ONLY thing that I ever added to Win 10 is the software to upgrade my Garmin.)

---

### Post by l33ch on 2018-11-04
Is there any swap usage?  I believe swap is there when memory gets low, so that could help you determine if it memory gets really taken up to determine if upgrading the memory or not. But honestly, I've never seen my swap taken up. Like others said, running VMs, or editing large audio/video files take up large amounts of RAM. Anything that needs an instant "scratch-pad" when working with large files.  Me personally, if I had 8gb of RAM and 5gb of it used (3gb free)...I wouldn't have much if I wanted to run any memory intensive programs/vms. You must have a bit of stuff loaded up on your particular rig. I would go with a leaner OS (if you are not intending to have stuff loaded/taking up RAM)  yeah, upgrade the RAM to 12 or 16gb total if you can. But I'm a little surprised because I have 8gb of ram with Ubuntu Studio 18(one of the larger footprint distros) and I'm only using about 1.3gb of RAM--granted this is with no VMs or wine apps running. But in my case, should I need to run 1-2 VMs or wine apps, I wouldn't be concerned because I have around 6gb avail. I would determine what is using up so much memory on your rig and decide if that is due in particular to what you are running/need to run. If yes, and that memory usage will be the same under any Linux, then yes I would upgrade the RAM. Otherwise, if whatever is using up the memory is not needed, or too much, then investigate alternatives for said program(s) and different operating platforms/systems (i.e. different linux flavors, etc).

---

### Post by mcsheffrey on 2018-11-04
Thanks for your feedback, with some good tips, but maybe I didn't word my question properly. what I would like to know is , will  ubuntu will take advantage of all the free memory that is available.It looks like its only using 1 additional GB of space, yet there is an additional 3 available. Would adding an additional 8GB allow it to use more of this memory for caching? (i.e. is he keeping that extra 3GB in case he needs it for processes?)  Hope this clarifies things.  Tks Roy

---

### Post by speartip on 2018-11-05
> **mcsheffrey said:**
> what I would like to know is , will  ubuntu will take advantage of all the free memory that is available.
No. Probably not. At the moment My Xubuntu machine which has been om all day, has 12GB Memory. Top is showing that 1.3GB is being used, & 1.8GB is being cached. Nearly 9GB is sat doing nothing. A year or so back I increased my machine's memory from 4 to 12GB, & noticed no performance improvement whatsoever.

---

### Post by mastablasta on 2018-11-06
> **mcsheffrey said:**
> Thanks for your feedback, with some good tips, but maybe I didn't word my question properly. what I would like to know is , will  ubuntu will take advantage of all the free memory that is available.It looks like its only using 1 additional GB of space, yet there is an additional 3 available. Would adding an additional 8GB allow it to use more of this memory for caching? (i.e. is he keeping that extra 3GB in case he needs it for processes?)  Hope this clarifies things.  Tks Roy

you need to change the swapiness. 
read:  [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

see under title: [B]What is swappiness and how do I change it?

[/B]that way you will use more ram instead of hard disk (or rather star using disk later). i did this on server with 4GB ram. it practically never touches the swap partition. that's important, since i am running the server from USB drive :) 

to add more ram is beneficial if tasks require a lot of read and write memory and you don't want them to use disk to do that (disks have miliseconds, ram has nanoseconds access speed).

---

