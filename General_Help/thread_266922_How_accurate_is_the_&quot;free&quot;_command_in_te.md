---
title: "How accurate is the &quot;free&quot; command in terminal?"
date: 2006-09-27
forum: General Help
---

### Post by Roasted on 2006-09-27
It says I'm using 1,600,000 (1.6 gb) of 2,000,000 (2.0 gb) yet, I have just FF and AIM open. When I go to system monitor, it says I'm only using 307 mb of memory. Obviously, 307 mb is more like it. Why does "free" in terminal say I'm using 1.6 gb?

---

### Post by neouser99 on 2006-09-28
identifing how much memory a system is taking up is a very very hard thing to do, and almost all utilities show something different. the one that i use the most often though is 'top' on the command line, and this usually reports the same thing that free does, which happens to be the same thing as /proc/meminfo, which happens to be maintained by the kernel.

even if you are using 1.6gb of memory, that still isn't 2.0gb of memory, which is what you want to be using. the kernel is usually very good at memory management, and you are probably losing sleep over something that isn't a problem at all. if you system has been up for a while, it just hasn't taken the oppurtunity to go free up memory if it doesn't need too.

-neo

---

### Post by RAOF on 2006-09-28
Interesting problems in identifying exactly how much memory you're using, or more interestingly, how much memory is available for applications (because they're definitely not the same thing).

First off, the kernel will cache disc accesses as much as possible, because ram is several orders of magnitude faster than the disc.  Do you count this cache as used ram?  If a program needs more ram, the cache can shrink essentially without overhead, so as far as programs are concerned the ram is essentially free.

Secondly, shared libraries.  For example: gnome-panel uses libgtk.  gnome-terminal uses libgtk.  Both gnome-panel and gnome-terminal have libgtk in their memory-range, so the memory used by libgtk is counted twice.  How do you know how much memory is shared between gnome-panel and gnome-terminal?  What about if gnome-terminal uses only a **part** of libgtk, and gnome-panel uses a different part?

It gets complicated quite quickly :)

---

