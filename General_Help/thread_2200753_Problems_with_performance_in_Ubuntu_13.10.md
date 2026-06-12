---
title: "Problems with performance in Ubuntu 13.10"
date: 2014-01-20
forum: General Help
---

### Post by ceciliasp on 2014-01-20
Hi,

I have a brand new ASUS VivoS400 Pentium Core i5 wth 4 gb of RAM and running Ubuntu 13.10.
I use my laptop mainly to browse the web (google chrome with many tabs at the same time), maybe a FTP  client and a text editor.
Since the last week I`ve been experiencing a decrease in the performance (screen freezing, slow reaction times, etc) after spending a certain amount of time using the computer (that means that the slow in performance doesn`t start right away but it takes at least 30 min. to begin experiencing the problem).

I don`t know what is causing the problem since I didn`t install any strange software. The only things I only install automatically are the system updates. Could that be what is causing the problem?

Please, if there is any other information needed to approach the problem, let me know.

Thanks

Cecilia

---

### Post by leclerc65 on 2014-01-20
I have a hunch that your computer swaps too much. 
With 4G RAM you can reduce the value of swappiness to 10 or less.
Also put your Chrome browser cache to RAM.

---

### Post by ceciliasp on 2014-01-23
Ok,.
[B]I´ll try that and report back-
Thanks for the tip[/B]

---

### Post by ceciliasp on 2014-01-23
So apparently there is a bug on the latest Chrome stable version: [http://ubuntuforums.org/showthread.php?t=2113179&highlight=chrome+freeze](http://ubuntuforums.org/showthread.php?t=2113179&highlight=chrome+freeze)
I am going to try disabling the hardware acceleration for now.
But another thing that draw my attention was this free -m output
                   total       used       free     shared    buffers     cached
Mem:          3839       3583        255          0         13        750
-/+ buffers/cache:       2820       1019
Swap:         3981        307       3674


Do you think would be solved by resizing the swap partition?
Should I do this running a Live USB stick?
Txs

---

### Post by leclerc65 on 2014-03-09
Sorry for the late answer. 
Just don't swap unless if you have to. Let the system use as much RAM as you can.

---

