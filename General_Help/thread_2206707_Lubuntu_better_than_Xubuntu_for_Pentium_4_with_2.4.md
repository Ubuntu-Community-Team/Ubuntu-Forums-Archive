---
title: "Lubuntu better than Xubuntu for Pentium 4 with 2.4GHz?"
date: 2014-02-20
forum: General Help
---

### Post by s1wood on 2014-02-20
I'm using a Pentium 4 with 2.4GHz with Xubuntu 12.04.

Looking at  system monitor I see that even with a few spreadsheets open but nothing  being done (apart from the system monitor of course)  the CPU usage is  level on 50% and just requesting printing pushes it up to 100%. 

Would Lubuntu give a significantly lower CPU usage? I don't want to change over if it won't make any real difference.


Susan

---

### Post by MG&amp;TL on 2014-02-20
I used to have a machine with a specification similar to yours. It ran both Xubuntu and Lubuntu tolerably, but it was *slightly* more responsive with Lubuntu. If I recall correctly, the real benefit of Lubuntu over Xubuntu is the memory usage: Lubuntu used considerably less.

I think the best thing to do would be to boot a live CD (or preferably USB) and see whether performance improves. Hypothetically, running off the storage medium shouldn't change the amount of CPU the operating system uses.

---

### Post by s1wood on 2014-02-20
Thanks. I'll try that. Memory doesn't seem to be a problem though.

Susan

---

### Post by s1wood on 2014-02-20
I've tried my Lubuntu 12.04 disc and since it doesn't have system monitor I had to look up the command line . Using 'top' the CPU usage was nowhere near as high, though there was a limit to what I could try.
I went back to Xubuntu and used top and opened everything I could think of and didn't get above 92% - even though system monitor was showing 100%.

Presumably the command line reading is the more reliable - if so it would seem I haven't really got a problem.

Anyone have any comments on that?

Susan

---

### Post by leclerc65 on 2014-02-20
I would reduce the Swappiness and put browsers' cache, Temporary files as much as I can to fill up that 1.5G RAM.

---

### Post by s1wood on 2014-02-20
Can you explain that a bit more, please?

Susan

---

### Post by MG&amp;TL on 2014-02-20
> **s1wood said:**
> I've tried my Lubuntu 12.04 disc and since it doesn't have system monitor I had to look up the command line . Using 'top' the CPU usage was nowhere near as high, though there was a limit to what I could try.
I went back to Xubuntu and used top and opened everything I could think of and didn't get above 92% - even though system monitor was showing 100%.

Presumably the command line reading is the more reliable - if so it would seem I haven't really got a problem.

Anyone have any comments on that?

Susan

Graphical tools tend to be less reliable than command-line tools, it's entirely possible that the system monitor is misreporting CPU usage. Based on the specification the machine is a desktop, so I guess what matters is whether there's any actual problems with it - does it feel 'laggy' or freeze for any noticeable period of time?

What the other poster is suggesting is to put temporary data that is usually stored on the hard disk into memory. The 'swappiness' is a value that instructs the kernel how much to 'swap' data between the RAM and a special file or partition on disk. If you have plenty of memory and your hard disk is slow, decreasing the amount of swapping can improve performance, but it shouldn't affect the CPU usage. You can read more here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq).

---

### Post by leclerc65 on 2014-02-21
A typical Ubuntu system uses about 500M of RAM. If the monitor show some swapping, when the memory is plentily available, that swapping is unnecessary.
You can reduce that by doing

sudo leafpad /etc/sysctl.conf

add the follwing lines
```
 
# Sharply reduce swap inclination
vm.swappiness=10
# Improve cache management
vm.vfs_cache_pressure=50

```

To put cache into RAM for Firefox do

In the browsing bar type : about:config 
set the value of the follolwing parameters as bellow
  
browser.cache.disk.enable 	        to false 
browser.cache.memory.enable 	to true 
browser.cache.memory.capacity     to -1 (or whatever value you deem appropriate)

---

### Post by mörgæs on 2014-02-21
Lubuntu 12.04 is out of support (and it wasn't really that good to begin with). If you decide to switch then 13.10 is a better choice.

---

### Post by s1wood on 2014-02-21
Thanks all,
I'll look into the 'swappiness'. The system works pretty well but can hang a bit sometimes.

Susan

---

