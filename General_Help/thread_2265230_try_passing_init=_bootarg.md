---
title: "try passing init= bootarg"
date: 2015-02-13
forum: General Help
---

### Post by chaoticpsyche2112 on 2015-02-13
I've looked at several threads that have the same issue and none of the solutions listed there have helped. the error i keep getting is

> mount: mounting /dev/disk/by-uuid/8fe953c1-7ec1-43e4-adf3-700cd5f5fb32 on /root 
  failed: invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting: /proc on /root/proc failed: no such file or directory
Target filesystem doesn't have requested /sbin/init.
no init found. Try passing init= bootarg.

busybox v1.21.1 (ubuntu 1:1.21.0-1ubuntu1) built in shell (ash)
Enter 'help' for a list of built in commands.

(inframfs)_
  

I've tried so many things, and I don't even know why this happened. I shut it down correctly for about a week, because I wasn't even at home. I booted it up to get some of my tax information, and then powered it back down but when I go to power it back up 2 days ago this is what I get. What's funny is that I was booting it up to do my backups of all that was on there... If this is a sign it's not very funny...

I have all of my music backed  up to this laptop... If I loose it I'm going to cry... Please help...

I have ubuntu downloaded onto the laptop, it runs nothing else. As of right now I'm posting from my tablet. 

When I tried some of the solutions others came up with ([here]("http://ubuntuforums.org/showthread.php?t=1386549")) nothing seemed to work. It kept giving me a list longer than what I was actually able to read. I've tried several other treads that had been linked into that one but still nothing lets me boot the accursed thing. I'm still looking around forums to see if there is a way around using live cd (seeing as I don't have a way to make a live cd at this time) or the boot from thumb drive... because I have absolutely no thumb drives... which is a bit awkward for me right now.

---

### Post by ajgreeny on 2015-02-13
This busybox problem occurred on my system a few years ago for no reason that I was aware of; no improper hard shutdown or power-outage; it just came out of the blue.

Luckily I did have backups for just such a happening, but even more luckily, running fsck on the root partition of the installed OS from a live system found and corrected some faults and got me back to a fully booting system again.  I have no idea how you could overcome this problem without booting to a live system, as I do not know how to use the busybox command-line nor what it is capable of doing, but it might be worth you searching for more info on how to deal with busybox and actually make use of it.

Or you could try borrowing a live DVD/USB of a Linux distro from someone, or even buying one from the advertisers on [www.distrowatch.com](www.distrowatch.com), and in future you should always keep one handy for exactly such situations.

---

### Post by Gvarelov on 2015-02-14
From that shell, try mounting root to /mnt. Then chroot to /mnt and start /sbin/init like "exec /sbin/init".

---

### Post by chaoticpsyche2112 on 2015-02-14
Gvarelov could you give me a step by step guide? I am horrible with coding... Truly atrocious if I were to be completely honest. I have no idea how to execute your original response that is why I am asking.

---

### Post by chaoticpsyche2112 on 2015-02-14
I know I should, and I normally do, but I finally finished moving from one plae to the other and when one moves around a lot they tend to forget where they packed most of their stuff... So I'm still sifting through all of my stuff, I know I have another thumb drive I just don't know where I have it. Hence the embarrassment and slightly awkward statement at the end of my original post. 

However, as the situation at hand is I don't have one available right now and am strapped for cash and so cannot get one.

---

