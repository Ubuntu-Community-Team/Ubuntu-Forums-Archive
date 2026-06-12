---
title: "reinstalling Do i have to do the swap Partition?"
date: 2014-08-22
forum: General Help
---

### Post by firas2 on 2014-08-22
so i am reinstalling to a different Partition     and would Like to know do i have to do this swap thing ??

I think i have more then enough ram    I have 16gbDDR3 

thank u

---

### Post by guccimucci on 2014-08-22
It depends what you want to do with your computer. If you have high ram and high hard disk space then you should be okay with around 2GB swap partition. Maybe this link is useful [http://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/s2-diskpartrecommend-ppc.html#id4394007](http://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Installation_Guide/s2-diskpartrecommend-ppc.html#id4394007)

---

### Post by firas2 on 2014-08-22
thank u i will look at the link but for a fresh guy like me    I have 16gb   so how much swap should i give please ???

I ask to make sure and get a second opinion 

many thanks

---

### Post by ajgreeny on 2014-08-22
It is difficult to know exactly what you are doing with your re-install using a different partition, but if you choose "Something Else" at partitioning stage of the install, which you must to be sure that all partitions on the disk are not overwritten, you can ignore any swap you already have and just let the new OS find it and use it automatically.

If you really do not want to have any swap, and thus delete any current swap partition you have, you will probably be fine, but even with such large amounts of ram a small swap of 2 - 4 GB is still recommended by most.

---

### Post by ibjsb4 on 2014-08-22
As an experiment you could just turn swap off and see how you get along without it.
```
sudo swapoff -a
```
[https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F](https://help.ubuntu.com/community/SwapFaq#How_much_swap_do_I_need.3F)

---

### Post by firas2 on 2014-08-22
Many thanks Guys  i was doing some reading here and there , finally I did find a Nice site that explains exactly , how to put linux on a partition  and boot from there .

But then i was looking around on the internet and I found a reasonable  128gb ssd  in my Local store so I ran out and got it :)  :) 

I will put Linux on the SSD and call it a day , and i will also go with the recommendation of 4gb  ram and if that does not work I will disable it  ,, just Like what [[COLOR=#000000]ibjsb4[/COLOR]]("http://ubuntuforums.org/member.php?u=1729120")[COLOR=#000000]  advicesd  

this way i have a clear head and every thing runs smooth ,, because I have windows 7 ultimate 64X as a raid 1  on 2 ssd's   and i really dont want to mess-up  My raid  :) :) 

many thanks and will do the swap    also if U guys think i should give more ram for swap  please let me know 

many thanks [/COLOR]

---

### Post by oldos2er on 2014-08-23
I have 8 GB RAM, and just a 512MB swap file rather than a partition. I don't run many memory-intensive apps so it's worked out fine for me.

---

### Post by ibjsb4 on 2014-08-23
Here's a way out idea :)

Do away with hdd swap and give a couple of gigs to zram.

---

