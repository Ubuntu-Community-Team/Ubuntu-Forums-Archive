---
title: "Should i enable zram and/or lower swappiness value"
date: 2014-02-01
forum: General Help
---

### Post by deaton25 on 2014-02-01
I use ubuntu 12.04 LTS. I have 2GB RAM. Now, that is split about 55-45 memory-swap. My CPU is almost flatlined!
Could I get faster leaner meaner more efficient performance if I lowered swappiness down to 10 and/or enabled ZRAM. Or should I leave well-enough alone? I am under the impression that zram is built into Ubuntu 12.04 and only needs to be enabled with a simple command. Should I do both together or should I do one but not the other?
Thanks

---

### Post by varunendra on 2014-02-02
I hope you already know that zram is a virtual swap within the RAM itself. I don't know if it is enabled by default or not, because I immediately upgraded my laptop from 2GB to 4GB when I bought it, and the first time I noticed the swap (cat /proc/swaps), it was already enabled.

From what I have seen so far, the default amount of zram is 50% of the available RAM, which means 1 GB for you. I have been VERY confused about how this 50% of RAM is allocated between zram and virtual ramdisk - **/run/shm**, because the size of /run/shm is also 50% of the total available RAM. I *think* it is shrunk as and when zram needs to 'Claim' the space allocated to it, but have no evidence of that so far.

But let's put the confusion aside (although I wish someone having clear understanding of these jumps in and explains it for us), and talk about your case. With only 2GB of total physical RAM, I wouldn't recommend to fiddle with zram. Even though it is compressible, I don't think you will gain much with it. On the contrary, the added complexity may even reduce performance when the demand for additional memory is high and the swap is actually needed.

You may safely try lower swappiness values (without zram), but I don't expect any significant gains from that either. The linux kernel is quite smart at managing the memory and usually the defaults are the best for an average user.

That being said, since different users have different needs and usage stats, and you can always go back to defaults if needed, feel free to experiment and enrich our knowledgebase with your valuable feedback. :)

---

### Post by vanquishedangel on 2014-04-01
Personally I love zram, and yes it should be worth it.

I will try to explain my rather limited knowledge of it


1. Zram is seen and used just like swap, actually it is swap. zram is just a term used for swap space that is on ram. Since ram is 100,000 times faster then a hard disk, using zram will be faster then regular swap. Zram also compresses the files that are swapped, this also causes it to use a little bit more processor power but has an effect of helping to extend your ram.


2.  The default setting in ubuntu for when to swap to zram or regular swap is 60 (I think this is a %, you can only set it from 0-100) This can actually be set to 10 (a setting of "0" will never use it, a setting of "100 wil always use it). If you set the setting to a lower number your computer will use swap less aggressively. To set the "swappiness" and see what yours is set at use these commands:

cat /proc/sys/vm/swappiness  (shows what is set)

sudo gedit /etc/sysctl.conf  (opens a text editor, add this line to the end of the file and save: **vm.swappiness = 10**)

(reboot your computer)


The trade off here is that because zram is run in ram it is a lot faster then swap space from a disk, but there can be a few caveats. Zram uses compression so this may eat some processor power. On devices with very little memory zram is excellent. The caveats to using zram are really not noticeable on devices with limited ram.

I have used zram on my android devices for years, my 2009 motorola smart phone ran pretty fast on newer androids thanks to zram. Android 4.4 now has it built in by default as part of androids memory management. So if it benefits old devices on android and ones with little memory, it will also help computers with Ubuntu.

---

