---
title: "Can Ubuntu run decently on a dual core 2 ghz 1 gb ram."
date: 2013-07-02
forum: General Help
---

### Post by phelenon on 2013-07-02
(solved) So I tried Ubuntu 12 on my laptop.It ran very slowly with Unity,was is because the swap was 300mb(it was a windows install:()?So I switched to Mint and it runs very fast.Now I want to goto Ubuntu again.Will it run fast.I usually have Skype, Pigden and alot of Firefox tabs open.Also my laptop has a overheating problem which was fairly disturbing in Ubuntu

---

### Post by sudodus on 2013-07-02
I think what you notice are differences due to the different desktop environments. It is the same Ubuntu engine under the hood of Linux Mint. Ubuntu's default desktop, Unity, needs a lot of memory and CPU horsepower to run nicely. I would say at least 2 GB RAM.

- What dual core is it? An old Intel dual core or an AMD dual core?

If you want to run Ubuntu, there are desktop environments with lighter foot-print desktop environments

- Lubuntu with the ultra light LXDE
- Xubuntu with the light XFCE

I suggest that you try these live (booted from an install CD or USB drive) and later on install the one with ***your*** balance between speed and eye-candy. After testing you should make a real installation, wubi is really only for testing.

If you want to keep Windows, you can make a dual boot system (install Ubuntu alongside Windows).

---

### Post by grahammechanical on 2013-07-02
I have an Intel Core 2 Duo 6600 @ 2.40GHz and 1GB of Ram. And the very latest Ubuntu runs very well on it. The key component is the video adapter. How powerful is the GPU and how much memory does the video adapter have. I have at least 2GB of swap. I will tell you this, with 12.04 basic RAM usage was about 70% of 1GB with just system monitor running. With 13.04 that was down to about 50% of 1GB.

Right now I am on Saucy Salamander with just Chromium running and the OS is using 518MB of memory with another 412MB set aside as cache memory. And only 209kB swap is being used.

I would not expect a great performance from Ubuntu when it is installed using Wubi.exe because it is running under another operating system. It does not have direct access to the hardware. Did you install Linux Mint as a proper dual boot? If so then you are not comparing like with like. Are you?

No operating system will be able to make up for deficiencies in hardware. 

Regards.

---

### Post by sanderj on 2013-07-02
> **grahammechanical said:**
> I have an Intel Core 2 Duo 6600 @ 2.40GHz and 1GB of Ram. And the very latest Ubuntu runs very well on it. The key component is the video adapter. How powerful is the GPU and how much memory does the video adapter have. 

I thought Ubuntu 12.04+ on 1GB was horribly slow. So, triggered by your post, I added "mem=1111M" to the grub boot menu of my "i3-2310M CPU @ 2.10GHz" running Ubuntu 13.10 with Mir, and now typing this in Chromium. Result:


```
sander@hapee:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1078        971        106          0          3        266
-/+ buffers/cache:        701        376
Swap:         4028         91       3937
sander@hapee:~$ 
```

... and ... it still works great. Very, very interesting.

FWIW: I have an Intel GPU, so I guess (?) no seperate GPU memory.

---

### Post by Bucky Ball on 2013-07-02
Heck, I have a P4 with a gig of RAM running Ubuntu Studio! Actually, that machine is a total hybrid about to be upgraded but it has 10.04 LTS on and Gnome, xfce, artwork from all over. 

Runs fine and I have had Skype and a heap of Firefox tabs and other stuff open plenty.

(The old admin machine has even lower spec AMD processor and was grinding out Ubuntu, under pressure, but with Skype and Firefox tabs. Ran well enough, better on Xubuntu, better still on a minimal install.)

---

### Post by sanderj on 2013-07-02
OK, for clarity: I'm talking about Ubuntu (13.10) with Unity on my forced-1GB system. That works well. Must be thanks to the i3 Core.

I already knew Lubuntu runs very well on a 1GB RAM system: I have it on a Celeron laptop here.

---

### Post by Bucky Ball on 2013-07-02
In that case you are talking about a testing version which is not released until October. Not really common fodder. ;)

---

### Post by 3rdalbum on 2013-07-03
Phelenon, Ubuntu 12.10 and later will only work well if you have graphics acceleration. Otherwise it will be a bit sluggish, although even that can be improved. What graphics card do you have?

In short, yes Ubuntu will run fine on that computer. You can also change the desktop environment to something lightweight, to get more speed.

---

### Post by phelenon on 2013-07-04
Thanks for all the help,sorry I was busy and did not check the thread.I have an Intel Dual Core 2Ghz.Ubuntu was a wubi install and Linux Mint was a proper one.I had tried Lubuntu and did not like it,it was too ugly.I have a decent Gpu.Another question was Ubuntu limited by the swap of 300 mb

Edit:I used Cinnamon with Ubuntu,it was fast but when I opened more than 4 Firefox tabs,it started lagging

---

### Post by sudodus on 2013-07-04
I think the lagging starts way before 300 MB of swap is used. But I would recommend, that you have more swap, 1-2 GB.

The lagging starts, when you have used all the RAM and need to swap out some of it to the hard disk, which is much slower than the RAM. I am not surprised that it starts when you have more than four tabs active in Firefox. There is only one solution to that problem: more RAM. But some people can accept closing tabs and using only one or a few.

If you want something with a foot-print between Lubuntu and Ubuntu, you can try Xubuntu and LXLE. They have slightly bigger foot-prints than Lubuntu because of more eye-candy. Anyway, it costs only your time (and if you enjoy testing, it is a low cost), to test several versions of Ubuntu and other linux distros until you find what is the best for you.

---

