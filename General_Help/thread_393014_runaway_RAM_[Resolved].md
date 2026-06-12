---
title: "runaway RAM [Resolved]"
date: 2007-03-25
forum: General Help
---

### Post by lukescheminger on 2007-03-25
Hello! I have a strange problem. Whenever I startup kubuntu everything is fine, and has normal RAM usage, but after a while, my system memory just gets eaten up, and I have no idea where it is going. 

Basically, I boot into kubuntu (6.10) and just let it sit, don't startup any programs or anything, but the ram usage will just keep going up until about 1,000,000 KB are used, and it says only 25,000 KB free. 

I used ksysguard to check the ram by the way, and when I try and look at which program is eating up the ram, it is not even accounted for by a program.

I'm not a complete noob, but still relatively new to linux (under 1 year). Any ideas?

---

### Post by jeffathehutt on 2007-03-25
As one person here said a while back, 'unused ram is wasted ram'.  I have a feeling most of that ram is being used as a cache, meaning it will be freed up as needed.  It's  normal for a linux machine to only have a few MB of free ram, so I wouldn't worry about it.

---

### Post by lloyd_b on 2007-03-25
> **lukescheminger said:**
> Hello! I have a strange problem. Whenever I startup kubuntu everything is fine, and has normal RAM usage, but after a while, my system memory just gets eaten up, and I have no idea where it is going. 

Basically, I boot into kubuntu (6.10) and just let it sit, don't startup any programs or anything, but the ram usage will just keep going up until about 1,000,000 KB are used, and it says only 25,000 KB free. 

I used ksysguard to check the ram by the way, and when I try and look at which program is eating up the ram, it is not even accounted for by a program.

I'm not a complete noob, but still relatively new to linux (under 1 year). Any ideas?

In a terminal window, run the "free" command.  Look at the line that starts "-/+ buffers/cache:".  If that line shows a large amount free, then you're fine - it just means that the OS is trying to take best advantage of free memory by using it to improve disk performance.

Lloyd B.

---

### Post by mcduck on 2007-03-25
jeffathehutt is right, Linux uses all free memory as disk cache to speed things up. When programs need more memory cache is reduced. 

To get real information about how much your applications are using RAM use the 'free -m' in a terminal, and then look at the '+/- buffers/cache'-line.

---

### Post by bettlebrox on 2007-03-25
As said before, there is probably a lot of caching going on which is usually a good thing. Have a look at this link about Linux memory usage:

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by aysiu on 2007-03-25
Read this:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by lukescheminger on 2007-03-25
Yep, you are all definitely right, thanks for the help. I didn't realize that it was being put to good use. Well, thanks alot!

---

