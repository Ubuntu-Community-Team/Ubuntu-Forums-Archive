---
title: "Performance Boost with 16 Cores?"
date: 2014-03-18
forum: General Help
---

### Post by mark114 on 2014-03-18
I currently have 2 HP DL 380 G5 servers with 2 quad core 2.6ghz processors (8 cores in all) and 4GB of ram.  One of these servers has developed a fault and I need another server el pronto.  Debating to get another of the same but with more ram but I have come across this server ...

HP ProLiant DL585 G2 **4x Quad Core 2.0Ghz 32GB RAM** SATA/SAS RAID Server Quad ESXi,

which, as you can see, has 4x 2ghz quad core processors (16 cores) and 32GB of ram.  My hard drives from my other servers will fit.

What I'm wondering is will I get a sufficient performance boost considering the amount of cores (16 as opposed to 8, albeit at a slower speed) and the extra ram?   Can my version of Ubuntu make use of the 16 cores?

My servers are running Ubuntu Server 3.5.0-47-generic (buildd@aallspice) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5).

---

### Post by QIII on 2014-03-18
Whether or not it will give you better performance depends on what you are doing with it.

Depending on how the kernel is compiled, what experimental stuff you use and the limitations of your hardware, I believe the max number of cores that can be used with the 64-bit server version is 4096.

A default server install can run 256 cores, I believe.

So, I think you're good!

Best wishes.

---

### Post by mark114 on 2014-03-18
> **QIII said:**
> Whether or not it will give you better performance depends on what you are doing with it.

The servers are running a lot of websites, many of which are database driven shops (comparision scripts), so a lot of database access is going on.  So, by the sounds of it, I WILL get a performance boost.

Thanks

---

### Post by startas on 2014-03-18
Or you could just take a look at usage of resources - cpu, ram, hdd, and if it reaches at least 90 %, then upgrade could help.

---

### Post by mark114 on 2014-03-18
> **startas said:**
> Or you could just take a look at usage of resources - cpu, ram, hdd, and if it reaches at least 90 %, then upgrade could help.

Well I'm running top to see where the load is and it is definitely mysql that is hitting the cpus.  %CPU is going way over 100% at times - unless I'm reading it wrong?  Memory usage seems ok.  16 cores should be able to handle the database requests more easily and thereby increase the speed of the shops.  I also intend to increase the number of shops quite a bit so by the looks of it I should get this new server.  Thinking about it it might well accept the processors from the other 2 servers making it 4x 2.6ghz.  Will have to enquire whether they will fit.

---

### Post by Impavidus on 2014-03-18
If CPU usage is going over 100% at times, it's adding the usage of the different cores up. With 8 cores it can go up to 800%. This will translate the 90% criterion mentioned by startas to a 720% criterion. Expect usage to become somewhat higher on the new, slower processors. No problem, they can handle 1600%.

---

### Post by mark114 on 2014-03-18
> **Impavidus said:**
> If CPU usage is going over 100% at times, it's adding the usage of the different cores up. With 8 cores it can go up to 800%. This will translate the 90% criterion mentioned by startas to a 720% criterion. Expect usage to become somewhat higher on the new, slower processors. No problem, they can handle 1600%.

That makes sense.  

Was humming and arring about which server to get but I made my mind up when I sourced a HP DL 585 with 4 x 2.4ghz quad core processors for not much more money than the 2ghz quad core machine.  Just bought it :D.  Might well get a HP DL 585 chassis with just ram and see if it will accept the 4 processors from the other servers and create a damn good backup machine.

---

