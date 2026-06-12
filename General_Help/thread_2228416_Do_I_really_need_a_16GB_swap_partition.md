---
title: "Do I really need a 16GB swap partition?"
date: 2014-06-07
forum: General Help
---

### Post by Mike1977 on 2014-06-07
So I just installed 14.04 on my new machine with 16GB ram. I initially wanted to set it up as 60GB dedicated to Ubuntu (on dual boot) set on my HDD. But the install instead set it at 43.5GB disk space, and gave 15.8GB to the linux-swap partition. I'm considering running off the live USB and shrinking the linux swap to something like 8GB, and extending the 43.5 to at least 50GB.  With this size of RAM, is it really necessary to have 16bg dedicated to swap partition?
Is all this even necessary? I mean I could just leave well enough alone. I have plenty of space available on exfat32 for files etc. 43.5 is probably more than enough for programs,right?
Thoughts?

---

### Post by coffeecat on 2014-06-07
Support thread.

*Thread moved to **General Help**.*

---

### Post by Mike1977 on 2014-06-07
I'm not asking for support. I'm asking for opinions.

---

### Post by LastDino on 2014-06-07
You don't. Are you planning to hibernate? If no, you can reduce that to as less as 2GB for curtsy. You're never going to use it considering you've 16GB of RAM.

It is safe to resize, but make sure you check if it is being detected when you boot into, if it isn't, let us know.

---

### Post by QIII on 2014-06-07
With 16GB of memory, there is really no reason to have any swap at all unless you plan to run 4 or 5 virtual machines at a time.

I don't have a swap partition at all on any of my machines with 8GB or more of RAM.

---

### Post by LastDino on 2014-06-07
> **QIII said:**
> With 16GB of memory, there is really no reason to have any swap at all unless you plan to run 4 or 5 virtual machines at a time.

I don't have a swap partition at all on any of my machines with 8GB or more of RAM.

Me neither, and I've only 4gigs (Though, I do keep swap around just in case). I think these online guides about partitioning should really start to address this.

---

### Post by Impavidus on 2014-06-07
With 16GiB ram you need at least 16GiB swap space, not 15.94GiB, to hibernate. But if you don't want to hibernate you don't really need swap.

About 20GB will be enough for your software. But all your files in your home directory are stored on that partition too, as you don't have a separate /home partition.

You've got a very large fat32 partition for data storage. Fat partitions are nowadays only really used on removable media (and efi partitions). Have you got any reason in particular for using that fat partition, mounted using the file manager, instead of an ext4 partition mounted automatically at /home?

Finally, on a 1TB drive I wouldn't worry about 10GB more or less in any partition in particular, as long as you're above the minimum.

---

### Post by philinux on 2014-06-07
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Please see this.

---

### Post by QIII on 2014-06-07
Respectfully, that wiki needs serious updates.  The largest amount of RAM it talks about is 2GB and 100GB of disk space.  Might be useful in that case -- but 8+ GB wasn't even considered.  

For hibernating, yes.  For practical purposes beyond that and considering the current State of the Art, no.

---

### Post by philinux on 2014-06-08
[http://docs.fedoraproject.org/en-US/Fedora/19/html/Installation_Guide/s2-diskpartrecommend-x86.html](http://docs.fedoraproject.org/en-US/Fedora/19/html/Installation_Guide/s2-diskpartrecommend-x86.html)

Indeed QIII. Some of it is still usefull info.

Found the above info.

---

### Post by philinux on 2014-06-08
[https://wiki.archlinux.org/index.php/partitioning#Swap](https://wiki.archlinux.org/index.php/partitioning#Swap)

And another view.

---

### Post by mikeyinid on 2014-06-08
With 16GB RAM, I wouldn't have any SWAP. Unless you're using hibernation, which is disabled in 14.04. No SWAP...

---

### Post by SuperFreak on 2014-06-08
One strategy to avoid using SSD space is to put SWAP on a Hard Drive partition instead of SSD

---

### Post by Mike1977 on 2014-06-10
Thanks everyone,
I shrank SWAP down to 2.5GB. I don't think I'll ever need it, but it's there for chance of later decisions. I moved over root to unallocated and all is well.

---

### Post by Luke M on 2014-06-11
Note that by default, linux uses swap even if you have plenty of memory. You can change this behavior by setting "swappiness" to 0, but if you don't have a swap partition, then you don't have to worry about it. So that's a little side benefit of not having a swap partition.

---

### Post by kurt18947 on 2014-06-11
> **Luke M said:**
> Note that by default, linux uses swap even if you have plenty of memory. You can change this behavior by setting "swappiness" to 0, but if you don't have a swap partition, then you don't have to worry about it. So that's a little side benefit of not having a swap partition.

There may be a benefit for the majority using non-UEFI/GPT configurations.  Swap uses one of four primary partitions.  That may or may not matter.  If I feel the need for swap, I set up a swap *file* rather than a swap partition.  I can't hibernate but I never used it when it was available (suspend or just shut down - Ubuntu doesn't take that long to boot).

---

