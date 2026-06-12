---
title: "Weird screenlets and apt-cache issue (possible security issue)"
date: 2008-03-08
forum: General Help
---

### Post by odiseo77 on 2008-03-08
Hello people. I installed screenlets on Gutsy some weeks ago from the following repository:

```
http://hendrik.kaju.pri.ee/ubuntu/ gutsy screenlets
```

Some days ago I noticed a strange CPU usage on the sysmonitor screenlet, so I executed ***top*** to see which process was eating my CPU and it was apt-cache. I didn't pay too much attention this time because the system was still usable, but when I woke up today I noticed the weird CPU usage again, checked with 'top' and it was apt-cache. I had to go out and left the machine running the whole day; when I came back, the issue was still there. so I restarted and it came back. Since I noticed the sysmonitor screenlet was freezing too, I killed the python process, then executed top again, and the apt-cache process was gone. Started screenlets again, and the problem came back; killed python and the problem disappeared. So, definitely there's something wrong with screenlets triggering the apt-cache command, but how (and why) in the world screenlets (or the sysmonitor screenlet) has to trigger apt-cache?

Something that might be relevant: the apt-cache command triggered by screenlets runs as my user (not as root) and changes its PID constantly (for example, I tried killing it with ***kill -9 pidof-apt-cache*** and I got something like *No such process*. Also, the weird CPU behavior I noticed on the sysmonitor screenlet was my the changing usage of my two cores (for example, core 1 goes to 99% while core 2 stays on 12 %, then core 2 goes to 99 % and core 1 stays in 12 %, something like that). 

Sorry if the above explanation is a bit confusing. If you have some doubt about it, please ask :-)

Does anyone have a clue of what might be wrong and whether or not am I possibly under some kind of risk? (I executed rkhunter and everything seems to be fine).

P.S.: the md5 and sha1 sums of the "/usr/bin/apt-cache" executable are the following, in case someone can verify in his/her own system:

md5 sum: fedc75f454b0f2b22429d3772a88978f  /usr/bin/apt-cache

sha1 sum: 36a5bee0ffe54d17dfdb73c7aa132e3b95bb0984  /usr/bin/apt-cache

Thanks a lot in advance.

---

### Post by Whise on 2008-03-08
try using the new screenlets version

---

### Post by odiseo77 on 2008-03-08
Thank you, Whise. I didn't know 0.0.13 was out. I removed '~/.config/Screenlets', installed version 0.0.13 and everything seems to be fine now. But, may I ask, do you know why apt-cache was triggered by screenlets before? :)

Thank you again.

---

### Post by odiseo77 on 2008-03-09
Well, after a few hours, the problem came back. When I woke up this morning there was the weird CPU usage and top showed apt-cache was running and changing its PID constantly, so I guess the problem is not solved. Does anyone have a clue about what might be wrong?

---

### Post by AhronZombi on 2008-04-26
ive noticed this problm with 0.1.1 whats this have to do with apt?

---

### Post by odiseo77 on 2008-04-26
I have no clue why it happened. Anyway, I installed Hardy and installed screenlets from the repositories; so far it's been working fine.

---

