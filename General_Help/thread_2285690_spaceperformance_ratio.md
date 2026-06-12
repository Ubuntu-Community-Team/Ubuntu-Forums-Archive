---
title: "space/performance ratio"
date: 2015-07-07
forum: General Help
---

### Post by James_Ryan_Stortz on 2015-07-07
*post deleted by author.*

---

### Post by James_Ryan_Stortz on 2015-07-07
*post deleted by author.*

---

### Post by kerry_s on 2015-07-07
the stuff you use.
install zram-config & your all set.

---

### Post by tgalati4 on 2015-07-08
Linux memory management is pretty good out-of-the-box, so unless you have a specific application or specific workload that needs improvement, I would leave RAM alone.  Open a terminal and post the output of:

```
free
```

---

### Post by v3.xx on 2015-07-08
You should of left your second post in there; it caught my interest as I run a [ubuntu session in ram]("http://ubuntuforums.org/showthread.php?t=1594694&p=9960597#post9960597") and am curious about your setup.

---

### Post by PaulW2U on 2015-07-08
> **v3.xx said:**
> You should of left your second post in there; it caught my interest as I run a [ubuntu session in ram]("http://ubuntuforums.org/showthread.php?t=1594694&p=9960597#post9960597") and am curious about your setup.

James_Ryan_Stortz deleted a lot of content in his second post for a reason only known to himself.

@James_Ryan_Stortz, do you still need help? Your deleted post can be restored if you so wish or the thread can be closed but deleting the entire contents of a post in a thread in which you have asked for help is unfair to those who have started to help or who have shown an interest in helping you.

Please let us know how you wish this thread to continue.

---

### Post by James_Ryan_Stortz on 2015-07-08
*post deleted by author.*

---

### Post by PaulW2U on 2015-07-08
Deleted text in post #2 restored.

---

### Post by tgalati4 on 2015-07-09
Well, that is an interesting Use Case.  But what ultimately matters is what applications does the User need to run in this environment?  I can see the basic kernel running with a 2D-layered file system split between RAM and compressed images on disk, but something like a browser with its large cache might choke with such a setup.

What is the ultimate end use for such a system?

---

### Post by James_Ryan_Stortz on 2015-07-09
*post deleted by author.*

---

### Post by James_Ryan_Stortz on 2015-07-09
*post deleted by author.*

---

### Post by tgalati4 on 2015-07-09
Well, your efforts illustrate the power of linux and open source software.  You can refactor the entire operating system or just the file system and make it do something different.  With solid state storage and some kernel tweaks, you should be able to run in smaller RAM footprints, with less power use and less memory management operations.

I would be curious to see the performance benefit of removing all compression from the file system and using larger static storage pools, while using smaller RAM footprints.  That would be a challenge.

---

### Post by James_Ryan_Stortz on 2015-07-09
> **tgalati4 said:**
> Well, your efforts illustrate the power of linux and open source software.  You can refactor the entire operating system or just the file system and make it do something different.  With solid state storage and some kernel tweaks, you should be able to run in smaller RAM footprints, with less power use and less memory management operations.


What nice words, thank you!

It's actually the power within computer technology itself because of logic. It's all built on mathematical principles, thus it derives these key qualities:

 * dependability
 * variability
 * scalability

Which means, in actuality, quite literally everything in the system is variable and scalable within a bound of consistent rules. We're literally just using electricity as a run-time for mathematical equations. It's essentially a calculator. Everything, including painting the pixels on your screen, is a logical procedure. So, if you can, using physical properties, in theory, accomplish a mathematical model, the computer is there to apply that --almost instantly! For instance, something that, although it would take forever, would be physically possible by hand, can be manifested by processing those instructions, giving us a new power, you could say. A new tool.

And it's true the unix-philosophy of "everything is a file" is quite a classic framework. Nothing wrong with it at all. It helps "unlock" that power, so-to-speak, by making those variables available (and within a structure.) I do, however, see some things that are not so favorable, (such as the cluttered "package-manager land" (/usr/share), etc.) but this is accountable to human-error, of course, and not these capabilities we've been blessed with.

Can you imagine trying to explain a laptop to somebody in Old Testament times? Who would have ever thought that we'd take that force behind the lightning that you see in the sky and put it in a box? Lol. Thank you Benjamin Franklin for standing outside during a thunderstorm and flying a kite! 

> **tgalati4 said:**
> I would be curious to see the performance benefit of removing all compression from the file system and using larger static storage pools, while using smaller RAM footprints. That would be a challenge.

I'd be very interested in that as well. I have read, though, that, due to the high-level of compression standard with squashfs (my images are less than ~40% original size,) the performance of reading less blocks significantly does outweigh the the overhead of decompressing, which is sufficiently fast. 

> **PaulW2U said:**
> Deleted text in post #2 restored.

@Fred Flinstone: Thank you for resurrecting this thread! Actually, you're from the stone-age, what kind of laptop are you using? You must literally be using "pidgin chat."

---

