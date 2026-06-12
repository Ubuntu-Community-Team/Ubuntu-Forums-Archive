---
title: "Why am I using swap?"
date: 2007-03-23
forum: General Help
---

### Post by FuturePilot on 2007-03-23
I have 2GB of RAM, so why am I using some swap? This doesn't seem to make sense.:confused:
```
             total       used       free     shared    buffers     cached
Mem:          2026        795       1230          0         20        342
-/+ buffers/cache:        433       1593
Swap:         3200          8       3191

```

---

### Post by djf_jeff on 2007-03-23
You are only using 8meg of swap, it's not that bad.

What is the uptime of the system? How many applications do you have open? What applications? Firefox is known to take many RAM when opened with a lot of tabs for many days.

---

### Post by stokedfish on 2007-03-23
Some apps rely on SWAP, nothing special.

---

### Post by Ramses de Norre on 2007-03-23
And the kernel doesn't release swap if it isn't necessary. Releasing swap takes some resources, so once used it stays flagged as used but everything important will be in your actual ram memory.

---

### Post by Jason_25 on 2007-03-23
Here's a link on adjusting "swapiness"

[http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html](http://www.brunolinux.com/06-Fine_Tuning_Your_System/Swappiness.html)

With that said, my systems with 2GB never seem to use swap.  I have systems with 1GB that don't seem to use swap.

---

### Post by FuturePilot on 2007-03-23
Thanks for the replies guys. The computer was only on for a little over 6 hours so, that seems odd to be using swap after such a short time.  And I really didn't have that much stuff running. At the time I just had Firefox, XMMS, Kiba Dock, and Beryl. I've also noticed that everything in Dapper seems to be more RAM hungry than Edgy. Nautilus was using like 30MB and I've seen Gnome Panel up around 100MB at times.

---

