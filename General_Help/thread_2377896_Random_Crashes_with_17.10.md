---
title: "Random Crashes with 17.10"
date: 2017-11-17
forum: General Help
---

### Post by remejuan on 2017-11-17
Switched over to Ubuntu a few month ago and after havign issues with Kubuntu 17.04 detecting my SSD during instalation I went with Ubuto 16.04 and everything was working fine, for the most part, only issue I had was never being alerted to low battery.

When 1710 cam eout I upgraded and for the most part things seemed OK, longer battery life, being told about low battery, but I soon noticed random freezing, entire OS completely locked up, nothing to do but force shut down, and I can see no correlation between the crashes, the best I could tell today when It froze like 5 times, they all happened when dealing with networking, either me going into the files and it scanning for network folders, switchign wifi networks or even going into network setting, but on none of the other occasions did I see such a seemingly direct correlation, the only thing that came up on google was an error in 1704 at some point where the OS would lock owing to the drive encryption, which I had used, so I thought maybe todays occurences where mearly triggers and that could be the root cause. It really is pretty random, it can go for a day or 2 without issue and then like today 3 times in 30 minutes.

Got home and installed Pop OS, another *Buntu flavour, looks nice but was not an hour before it locked up again, and I was nowhere near networking, I had a browser and a terminal open as I was busy installing stuff.

So while the ultimate goal here is to try and fix the problem, for starters I would appreciate some help in simply debugging so I can work out the actual cause, that will hopefully make finding the solution much easier.

I guess maybe some hardware specs may help.

MIS GE72 2QL
i7 i7-5700HQ 
GTX950 Nouveau Drivers (The official Nvida ones turned my 3h battery into a 30min battery)
Samsung Evo 850 120GB

Thanks

---

### Post by ian-weisser on 2017-11-17
Note the time of a freeze.
Later, look in /var/log/syslog for the time of the freeze. Any error messages logged?

---

