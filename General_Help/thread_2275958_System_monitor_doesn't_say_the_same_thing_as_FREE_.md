---
title: "System monitor doesn't say the same thing as FREE command for RAM usage."
date: 2015-04-29
forum: General Help
---

### Post by sebastiaan5 on 2015-04-29
Lenovo y50-70 16gb ram ubuntu 14.04

this is my output for "free" command in terminal.
```

 total       used       free     shared    buffers     cached
Mem:      16344016   12781308    3562708     674088     204808    9900484
-/+ buffers/cache:    2676016   13668000
Swap:     24414204          0   24414204


```

and my monitor says I’m using only 2.5gib out of 15.6.

Which is the right one to look at to see my usage of RAM memory? 

greetings

---

### Post by v3.xx on 2015-04-29
"free" agrees with your system monitor.
Maybe this will explain better.
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by sebastiaan5 on 2015-04-29
So System monitor is the right one to look?

---

### Post by deadflowr on 2015-04-29
Compare the +/- buffer/cache line and not the top line of free.
You can also use one of the options instead of just free, like
```
free -m
```
which will show the output in megabytes.
or
```
free -h
```
which will show a more human-readable output.

---

### Post by v3.xx on 2015-04-29
> **sebastiaan5 said:**
> So System monitor is the right one to look?
They are both correct as deadflowr has pointed out.

With 16G of ram, your going to have to try hard to use it up.  I got things like conky, compiz, virtualbox, ram drive going on and my norm is about 10G of used ram.

You don't really need swap with this much ram, but I run 2G of swap and have swappiness set to zero.

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

[http://ubuntuforums.org/showthread.php?t=1594694](http://ubuntuforums.org/showthread.php?t=1594694)

---

