---
title: "Would Yahoo mine bitcoins on my machine?"
date: 2019-01-24
forum: General Help
---

### Post by ffrr on 2019-01-24
Hi
I am experiencing episodes of memory overload when the machine slows down to reaction times on the order of half a minute. The system monitor then shows memory over the top, heavy CPU activity and continuous network traffic when I am doing absolutely nothing. Just now the system monitor displayed an ominous memory-usage pattern of periodic ascending fills for ten seconds or so up the top of available memory and then dropping down abruptly to perhaps 95 percent of available memory, the CPUs and networking very busy all the time. Obviously, data were, in cycles, being generated, accumulated in memory and then dumped. Next I closed a tab in Firefox that was running Yahoo ([https://finance.yahoo.com/quote/LOGN.VX](https://finance.yahoo.com/quote/LOGN.VX)) and the system monitor immediately ceased to display the hectic symptoms of an obvious highjacking. I don't suppose Yahoo would do a thing like that. It would still act as a vector infecting my machine with the pathogen. Comments, hints, suggestions welcome.

---

### Post by QIII on 2019-01-24
Hello!

You could use top or htop to monitor CPU and memory usage for a time and see what processes are taking up resources during those peak times.

---

### Post by Autodave on 2019-01-24
I had very similar problem with one of my machines.  I treied running AdBlocker, but that made it worse.  Someone here suggested that I switch to *uBlock* (add-on in Firefox) and that seemed to fix everything.

---

### Post by ffrr on 2019-01-25
To QIII. Good advice! I have been looking at processes but haven't been able to identify their originators, let alone telling the staff from the marauders. 
To Autodave. I am using AdBlocker indeed. Following jour suggestion I disabled it and downloaded uBlock. Let's see what happens. Thanks for the hint.  [FONT=arial][/FONT]

---

### Post by Holger_Gehrke on 2019-01-25
Another useful Add-On to have is "NoScript". It allows you to select Javascripts by origin and either execute or block them. It took a while until I had everything I use regularly sorted out so the sites worked right. Opening a link to a site I've never visited before is a bit of a pain since it blocks unknown script-sources by default, but in my opinion it's worth it.

Holger

---

### Post by ffrr on 2019-01-31
Holger: Thanks for pointing out NoScript. I suppose the way to use it is to activate it before opening an unfamiliar page. Nothing shows because Ublock blocks everything by default. Then activate NoScript, unblock the names that look like the wanted ones. See if the loading page is functional. If not, deactivate NoScript. The names that remain blocked won't have a chance to run their scripts.

Frederic

---

