---
title: "random freezes during boot"
date: 2007-02-15
forum: General Help
---

### Post by theophane.weber on 2007-02-15
Hi,

I tried to get some help earlier (on the absolute beginner forum) for a mount root filesystem hang-up during boot; and i understand it's too time consuming for someone to look in detail and/or not a complete beginner issue.. So, I was wondering if I could just get some help to find how to solve it myself:

Randomly (not always but sometimes, without changing anything to the system), ubuntu freezes during boot at "mounting root file system" - the second line of the "graphical boot procedure" (the information given concerning boot, while that little bar keeps going left to right and so on..)

what does it mean that mount root filesystem fail? Or, more precisely, how can it fail? My ubuntu partition is the very first partition of my first disk. 

a) how is it possible that the sucess of mounting the root fs is random? Without changing anything in the configuratino of anything, if i keep rebooting for fun, it will sometime go past the root fs, sometimes not. i am used to more.. "deterministic" computers.

b) what happens exactly when the root filesystem can't mount? Does it mean it can't find the hard drive? the partition? 

c) when it is stuck at "mounting root filesystem", how can i stop it from trying to mount the fs? How can I diagnose what is exactly going on? Is there any way I can get a full text boot information (to know what precisely causes the system freeze)?

I am not a complete beginner, and far from a experienced user.. I have used different versions of ubuntu (edgy, warthog, and currently dapper). They all work fine on my computer, except for that annoying detail.

Thanks for any help!

---

### Post by kdub432 on 2007-02-15
I had this problem, more or less.... first of all, you might want to pop in a live cd and run the command 'fsck' on the hard drive to scan for file system corruptions... (just hit y if it ask questions....) 

when i had this problem, fsck died with some weird error... which means you need a heavy-duty hard drive repair program...I used a program called spinrite, which basically checks the entire surface for errors, (surface and data errors). Its a pretty automated process with spinrite, but it takes a long time. I had massive file corruption on track 0 of my hard drive, which it corrected, fortunately. I'm sure there are other alternatives to spinrite, though, (unfortunately spinrite is a commercial program....) 

after that you need to run fsck again, just to sort things out. 

but that should do it :-D

---

### Post by theophane.weber on 2007-02-15
can this happen with a completely new system ? My installation is one day old. And actually, it did the same on two different hard drives (I used to have ubuntu on a different slower drive b/c Ubuntu would just not like the other hard drive I had.. it seems it likes it more since dapper) . I did a quick format, but i assume that when you say "file system problem", it is a system, not a hardware problem

---

### Post by theophane.weber on 2007-02-15
fsck reports everything is clean. i am puzzled...

---

