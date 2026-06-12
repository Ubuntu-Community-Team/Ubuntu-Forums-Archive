---
title: "how to remove snappy or snapd"
date: 2016-06-17
forum: General Help
---

### Post by wheelie207 on 2016-06-17
How do I remove the snappy core or snapd from my ubuntu 16.04.
I have no interest in the snappy crap and want to remove it from my box, but have not found any solution to it.
I have my reasons and feel that it will be a problem with security issues.
I do hope that I can remove it or is ubuntu going to start acting like microsoft and force everything on us.

So I hope there is a way to remove it from my box. Thanks

---

### Post by grahammechanical on 2016-06-17
I was going to help you but I have my reasons for not giving assistance.

---

### Post by wheelie207 on 2016-06-17
Well, then you should of not said anything.
If I can't remove it, then maybe it's time to change to another distro.

---

### Post by mc4man on 2016-06-17
By default snapd does nothing much in 16.04 & no one is forcing anybody to use snap packages. To remove - 
```
sudo apt purge snapd ubuntu-core-launcher squashfs-tools
```

---

### Post by wheelie207 on 2016-06-17
Thank you very much.

---

### Post by ajgreeny on 2016-06-18
Great. Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by Jay_E on 2017-03-03
Another Thank you.
I have an old HP-mini running Ubuntu 16.10
At startup, it had 6 instances of snapd running and the machine was thrashing, and swapping to swap.
Remving snapd cleared this up.
Thanks, Jay

---

### Post by bandjc on 2017-07-01
> **mc4man said:**
> By default snapd does nothing much in 16.04 & no one is forcing anybody to use snap packages. To remove - 
```
sudo apt purge snapd ubuntu-core-launcher squashfs-tools
```

Thank you very much. Tried to use snaps this evening and they almost bought my machine to a standstill (and none of them worked!) 
I'll leave snaps alone in future, after following your instruction above..
Cheers,
Bwucie

---

### Post by tntteam on 2017-07-06
> **mc4man said:**
> By default snapd does nothing much in 16.04 & no one is forcing anybody to use snap packages. To remove - 
```
sudo apt purge snapd ubuntu-core-launcher *squashfs-tools*
```

Thanks, I wish there was a list of these uneeded packages to remove... Btw, I didn't remove squashfs-tools because it asks to remove lxd by dependancy.

I understand you put all these things in client distrib, but why in server distrib ? It deserve you a lot to install non wanted software on supposed secure server distrib. My 2 cents.

---

### Post by renaissance7449 on 2017-11-18
Thanks

---

### Post by purplesuit123 on 2018-01-13
Thanks to those who provided the answer.  When I load a new distro, boot it for the first time, and see a connection to api.snapcraft.io port 443, I stop work until that vulnerability is removed.  Life in the OS world is difficult enough without stuff like that.

---

