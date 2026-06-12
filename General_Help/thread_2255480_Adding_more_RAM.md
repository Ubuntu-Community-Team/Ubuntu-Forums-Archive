---
title: "Adding more RAM?"
date: 2014-12-05
forum: General Help
---

### Post by Gordonbp531 on 2014-12-05
I have an Acer Aspire E3 with 4GB RAM - 3.7 useable.
Looking at System Monitor, it never seems to use more than 75-80% of available RAM (and often considerably less), and only a very small amount of the 15GB Swap.
As it's going to cost me £60 to upgrade to 8GB (the only upgrade option), is it worth it, given the usage above? Will I notice much (if any) increase in performance?

Can I get a report out from a log somewhere that will give me a better picture than the limited time-frame of System Monitor?

Thanks.

---

### Post by buzzingrobot on 2014-12-05
Since you seem to be using little or no swap, I'd say it's a tossup. 

As you know, space on the swap partition is used, simplifying, when the system tries to load more bits into RAM than are available at that moment. (Available RAM varies constantly, depending on the applications in use, what they're doing, etc.) Because pushing bits to and from a physical disk is so much slower than pushing them around in RAM, prolonged use of swap becomes obvious because the system will become slower.

If a system is swapping enough to be annoyingly slow, the two ways to fix it are to add more RAM or to load fewer applications/fewer files at one time.

This link notes some common ways to get a finer-grained look at memory use: [http://www.binarytides.com/linux-command-check-memory-usage/](http://www.binarytides.com/linux-command-check-memory-usage/). Martin Wimpress, the lead on the Ubuntu Mate effort, did a detailed comparison of memory use on different interfaces a while back, and outlines his method here: [https://flexion.org/posts/2014-03-memory-consumption-of-linux-desktop-environments.html.]("https://flexion.org/posts/2014-03-memory-consumption-of-linux-desktop-environments.html#")

---

### Post by ajgreeny on 2014-12-05
Why have you got 15GB swap when you've only 4GB ram?

Actually, unless you're doing a lot of very intensive graphic work eg. video encoding, or have virtual machines running alongside the host OS, 4GB ram is probably enough, and I think 15GB swap is over-the-top.
Do you notice the machine runs slowly at times, or is this an enquiry in advance of problems occurring in future.

---

### Post by Gordonbp531 on 2014-12-05
> **ajgreeny said:**
> Why have you got 15GB swap when you've only 4GB ram?



Future-proofing! My aim initially was indeed to upgrade to 8GB RAM....maybe 15GB was a bit much - possibly 12GB would have been sufficient.


> **ajgreeny said:**
> 
Do you notice the machine runs slowly at times, or is this an enquiry in advance of problems occurring in future.

Doesn't *seem to*, I've generally found (certainly in the Windows world) that manufacturers tend to err on the low side of RAM...however, it seems that this one is as you say, probably OK.

---

### Post by Gordonbp531 on 2014-12-05
Thanks - I'll take a look at those links.

---

### Post by kpatz on 2014-12-05
Ubuntu in general uses less RAM than Windows.

For light use 1 GB is adequate and 2 GB is good.  You probably won't need more than 4 GB unless you do heavy image editing, gaming or host VMs.

You may want to turn down your swappiness in your /etc/sysctl.conf file, to something like 10, to reduce the use of swap.  That'll speed things up some.

---

### Post by Gordonbp531 on 2014-12-05
> 

You may want to turn down your swappiness in your /etc/sysctl.conf file, to something like 10, to reduce the use of swap.  That'll speed things up some.

Can't see anything in that file about swap - it all seems to be about networking and ipv4 and 6...

---

### Post by kpatz on 2014-12-05
You have to add the line to /etc/sysctl.conf yourself.  So edit the file as root using whatever text editor you prefer, and at the bottom, add the line:

```

vm.swappiness = 10

```

Save the file and reboot.  You can check your current swappiness setting with the command **cat /proc/sys/vm/swappiness**.

If you want to change the swappiness without rebooting, use the command **sudo sysctl vm.swappiness=10**.  You'll still need to edit /etc/sysctl.conf if you want your new swappiness to be applied next time you boot.

---

