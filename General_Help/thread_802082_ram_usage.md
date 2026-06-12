---
title: "ram usage"
date: 2008-05-21
forum: General Help
---

### Post by insurin on 2008-05-21
I only have a p4 2.4 ghz with 1 gb ram

My performance monitor is indicating to me that ram usage is always 800-900mb and my cpu is always fluctuating 0-50.

I have kde desktop and firefox 3 and swiftox running most of the time.

Is this normal usage?

---

### Post by mali2297 on 2008-05-21
In a terminal, type
```

free -m

```
Post the output.

---

### Post by insurin on 2008-05-21
total 1009 used 921 free 87

I also have ssh server running, in fact amarok is probs running as well as kopete

---

### Post by mali2297 on 2008-05-21
Did you look at the second line, -/+ buffers/cache? That's the relevant usage.

---

### Post by mali2297 on 2008-05-21
To view the ten most memory-consuming processes, you can use the following chain of commands:
```

ps -eo pmem,comm | sort -nr | head

```

---

### Post by insurin on 2008-05-21
> **mali2297 said:**
> To view the ten most memory-consuming processes, you can use the following chain of commands:
```

ps -eo pmem,comm | sort -nr | head

```


 9.8 firefox
 3.7 amarokapp
 3.1 kopete
 2.8 Xorg
 1.7 python
 1.7 konqueror
 1.7 konqueror
 1.7 kicker
 1.6 kded
 1.5 katapult

2nd line

-/+ buffers/cache:        323        685



why is konqueror running if I use doplhin for file browsing?

---

### Post by mali2297 on 2008-05-21
> **insurin said:**
> 9.8 firefox
 3.7 amarokapp
 3.1 kopete
 2.8 Xorg
 1.7 python
 1.7 konqueror
 1.7 konqueror
 1.7 kicker
 1.6 kded
 1.5 katapult

2nd line

-/+ buffers/cache:        323        685



why is konqueror running if I use doplhin for file browsing?

The memory usage is normal (for Kubuntu). To see which processes are cpu-intensive, you can run
```

ps h -eo pcpu,comm | sort -nr | head

```
or (to view it in real time)
```

top

```

Do you feel that the system is slow?

---

### Post by kerry_s on 2008-05-21
> **insurin said:**
> I only have a p4 2.4 ghz with 1 gb ram

My performance monitor is indicating to me that ram usage is always 800-900mb and my cpu is always fluctuating 0-50.

I have kde desktop and firefox 3 and swiftox running most of the time.

Is this normal usage?

for kde that would be about normal, kde starts everything, doesn't matter if you use it or not, thats how it gives a speeder feeling, the stuff is already buffered to ram. the cpu is because it checks to make sure it's parts are in ram, kde parts are never moved to swap. you should read up a little on kde to understand what your using and how it works.
to get the most from kde, you really want to use the kde programs, like konqueror and koffice, kpdf, etc...

---

### Post by insurin on 2008-05-21
thanks for the informative replies. I Have learned some useful commands and a bit more about kde

---

