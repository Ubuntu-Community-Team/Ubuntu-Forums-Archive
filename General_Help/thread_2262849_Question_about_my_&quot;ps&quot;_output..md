---
title: "Question about my &quot;ps&quot; output."
date: 2015-01-27
forum: General Help
---

### Post by Bobby_James on 2015-01-27
How is it possible for one program to be using more than 100% of the CPU?


USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND

me          24606     132     8.0    1356856    474012 ?         Rl      18:27     16:45 

/usr/lib/firefox/plugin-container /usr/lib/flashplugin-installer/libflashplayer.so -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 5984 true plugin

---

### Post by Holger_Gehrke on 2015-01-27
100 % is one fully utilized core. On a multi core processor a multi threaded program can utilize multiple cores and therefore use more than 100%. On a system running under any kind of load the sum of the percentages is usually way bigger than 100% up to 100% multiplied by the number of cores.

---

### Post by Bobby_James on 2015-01-27
Thanks! How would I find out how many cores my system has?

---

### Post by SeijiSensei on 2015-01-27
There are many ways, but the most informative is to run the "top" command, then press "1".  It will show you the load on each core.

---

### Post by Bobby_James on 2015-01-28
I have cpu0, cpu1, cpu2, and cpu3, so presumably four cores.

Thanks for your help - much appreciated.

---

