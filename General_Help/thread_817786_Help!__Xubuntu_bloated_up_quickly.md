---
title: "Help!  Xubuntu bloated up quickly?"
date: 2008-06-03
forum: General Help
---

### Post by zggame on 2008-06-03
Hi,  I have installed Xubuntu 8.0.4 on my old Dell laptop, PIII 1.2G/512M/30G.   When I just installed, it runs with about 300M ram taken without running anything according to top. And it takes no swap with 10+ tab with firefox and a couple of terminals.   But after a couple of weeks, it starts with 450M ram taken and constantly takes 100M swap although the CPU load is still not fairly low according to top.  I installed a few packages, (vsftp and mlnet, but not running at the start, some music player such as VLC, mplayer, netbean with java).  But I assume none of them should start at the beginning.  I know this question is kind of vague and has no quick answer.  I am wondering if anyone can point me to some places that I can start to read and optimize my system.  Thank you.

---

### Post by Rocket2DMn on 2008-06-04
You can always turn off unneeded services from System->Administration->Services, though I prefer to use a different program for this called Boot-Up Manager since it is more advanced.
```
sudo apt-get install bum
```
You can access that from System->Administration->Boot-Up Manager
Here are some other nice links, too:
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by zggame on 2008-06-04
> **Rocket2DMn said:**
> You can always turn off unneeded services from System->Administration->Services, though I prefer to use a different program for this called Boot-Up Manager since it is more advanced.
```
sudo apt-get install bum
```
You can access that from System->Administration->Boot-Up Manager
Here are some other nice links, too:
[http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)
[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Thanks.  I shut down a few services and the idle system go back to around 300M ram.  The boot up trick does not do much for me though.

---

