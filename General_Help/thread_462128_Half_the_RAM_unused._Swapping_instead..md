---
title: "Half the RAM unused. Swapping instead."
date: 2007-06-02
forum: General Help
---

### Post by tro on 2007-06-02
I've got 1 GB of RAM on my Thinkpad T60 running Feisty. The kernel sees all the RAM, but whenever I try to use more than about 512MB swapping occurs. If I keep opening new applications it keeps swapping and completely ignoring the remaining 512MB of RAM that's available.

Could it be some of these mounted partitions? Here's my df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              72G   26G   43G  38% /
varrun                502M  160K  502M   1% /var/run
varlock               502M  4.0K  502M   1% /var/lock
udev                  502M  116K  502M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   33M  470M   7% /lib/modules/2.6.20-15-generic/volatile
```

AFAICT, devshm is tmpfs, which means that it shouldn't "reserve" RAM and it can get swapped out to disk if there's memory pressure. What about the other partitions? What's lrm?

What else can cause this? I'm running Trevino's suspend2-modified kernel, but AFAIK it only gets patched with suspend2 patches and nothing else.

---

### Post by reclusivemonkey on 2007-06-03
> **tro said:**
> I've got 1 GB of RAM on my Thinkpad T60 running Feisty. The kernel sees all the RAM, but whenever I try to use more than about 512MB swapping occurs. If I keep opening new applications it keeps swapping and completely ignoring the remaining 512MB of RAM that's available.

Have you tried a memtest?

---

### Post by yabbadabbadont on 2007-06-03
[http://en.opensuse.org/Responsiveness](http://en.opensuse.org/Responsiveness)
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)
[http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems](http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems)

Read through those while paying close attention to the parts that refer to "swappiness".

---

### Post by tro on 2007-06-05
> **reclusivemonkey said:**
> Have you tried a memtest?

Yes. Memtest86+ doesn't show any errors after 2 passes.

> **yabbadabbadont said:**
> [http://en.opensuse.org/Responsiveness](http://en.opensuse.org/Responsiveness)
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)
[http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems](http://wiki.linuxquestions.org/wiki/FAQ_-_Linux_problems)

Read through those while paying close attention to the parts that refer to "swappiness".

I set swappiness to 0, but I'm observing the same behaviour. Whenever the memory use approaches 500megs, swap starts to be used instead of RAM.

Any other ideas?

---

### Post by tro on 2007-06-05
This is what "free" shows as memory use is approaching 500MB and swap is starting to be used:

```
             total       used       free     shared    buffers     cached
Mem:       1026440    1012972      13468          0       2216     547652
-/+ buffers/cache:     463104     563336
Swap:      2096472      42068    2054404

```

Note that there's about half my RAM "cached".

---

### Post by tro on 2007-06-05
I think VMWare 6 Workstation is the culprit. When I start a VM in it and watch the memory usage in htop, I see the cached level in memory increase significantly (till the end of the bar). So I guess instead of "using" the memory, it just "caches" it for itself or something.

It fooled me 'cause gkrellm showed only 500MB actually "used".

---

### Post by sra136 on 2007-07-22
Hello,
I have been experiencing the same situation as tro.  I have a gig of ram on my notebook.  When approaches 500mb, ~470mb is processed by RAM and ~30 or so mb's used processed by Swap.  If I have 1 GB of memory, why is the Swap used at all?  

Thanks!

---

### Post by Old Pink on 2007-07-22
Try turning your swap off and seeing if it'll pass 500. :) 

```
sudo aptitude install gparted
```
Then System > Administration > GNOME Partition Editor
Go the hard drive with the swap, right click the swap and click swapoff.

One of your 512 sticks could be broken.

---

### Post by sra136 on 2007-07-23
In System Monitor, my total memory is listed as 1003.3.  If  a RAM stick is broken, wouldn't it NOT show up?

Thanks!

---

