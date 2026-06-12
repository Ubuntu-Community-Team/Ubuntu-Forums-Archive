---
title: "Partitioning problem"
date: 2007-04-21
forum: General Help
---

### Post by clip.fest on 2007-04-21
Hello,
I'm a newcomer to this whole Linux thing, and despite considering myself an experienced PC user, I really don't want to risk losing my current Ubuntu installation, so here I am asking for help. I did look around in these forums, but failed to find a similar problem.

So, here's the thing (boring details here):
I bought a new laptop (HP dv2385ea) with Vista on it, and installed Ubuntu (after borking SUSE :P). I'm happy with Ubuntu and it soon became my OS of choice on that computer (since I really didn't like Vista, and had little time to install XP over it).
Yesterday, I finally took the time (and the trouble... because it involved a custom XP disc, don't ask) to remove Vista and install XP with my usual set-up, which involves 2 partitions - one for Windows and another for Settings. All went well, and after some failed attempts to recover GRUB with my Ubuntu Live CD, I finally recovered it with the Super GRUB Disc.

Now, the bad part...
Since I used two primary partitions to install XP, my HDD got "full", because I reached the 4 primary partitions limit - Windows uses 2, Linux one (extended partition with 3 logical partitions), and the last one is the HP recovery partition (which I don't want to remove unless necessary, because I might want Vista back someday, although I don't know if that partition can be used to recover Vista :P).
So, because of this I couldn't use the unallocated ~100GB left on my HDD.

Partition structure at this point (all is working):
> [primary]___[primary]___[unallocated]___[extended [linux-swap] [/] [/home] ]___[primary]

I used Hiren's Boot CD to do this (only XP works):
> [primary]___[extended [xp_settings] [xp_swap] [data] [linux-swap] [/] [/home] ]___[primary]

After using SGD again, I got GRUB back, and I can boot Windows with no problems, but Ubuntu won't boot :(

I tried using Ubuntu Live CD to edit GRUB's menu.lst and point the Ubuntu entry to the correct partition, but still I can't boot into Ubuntu (I assume this is because the partition order changed).
After some searching around here I found about SystemRescueCD, but don't really know how to use it to solve this problem, and this is where I hope someone can enlighten me.



Sorry for the long post and the amount of useless information, but I'm so fed up of trying to sort this out that I ended up ranting here.

---

