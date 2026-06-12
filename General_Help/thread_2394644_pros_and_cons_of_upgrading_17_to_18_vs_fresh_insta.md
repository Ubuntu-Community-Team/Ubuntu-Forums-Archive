---
title: "pros and cons of upgrading 17 to 18 vs fresh install 18"
date: 2018-06-19
forum: General Help
---

### Post by seekertom on 2018-06-19
Just wondering whether I should upgrade my ver 17 to 18.04 lts, hopefully keeping all my stuff, or do a fresh install from iso...

If upgrade, am I keeping any residual baggage best left behind? etc

thanks!
st:D

---

### Post by yancek on 2018-06-19
If you do not have a lot of configuration settings you want to keep, a new install is a lot easier.  It also takes longer to upgrade in my experience, 3-5 times longer.  
Another factor is do you have a separate /home or /data partition?  If so you can keep that when you do a new install.

---

### Post by seekertom on 2018-06-21
i think this is my big weak point: during install, selecting something else option, i run into so many options that i do not know enough about to make a comfortable decision, especially things like setting up new partition, especially starting points, like home, root, or whatever. these are the areas i really need to drill down into so i feel as competent as i was in winduz. still, any nudges from yall certainly help me, and are greatly appreciated.
thx, st

---

### Post by bodhin2 on 2018-06-21
i too have tried to follow all sorts of directions about keeping a separate home partition.  may have been successful once but when i did upgrade with another distro i lost it all.  now i keep it simple and do the basic generic install.  use LTS and you are good for 5 years or so.  when times comes make sure all - all - all  stuff is backed up to external drive or usb stick - i do redundant backups - and then spend a day or so tweaking.  I also tried to write down all tweaks etc so i know what i need generally the next time.  though things may change by then.

---

### Post by Dennis N on 2018-06-21
I am now opting for upgrade over new install, and have had success with all the upgraded OS from 17.10 to 18.04 that I did (5 on several different computers). Also did a 14.04 to 16.04 with intent to take the next jump to 18.04 when available for LTS. The differences in upgrade time mostly depends on factors like the processor power and drive write speed (package download time is similar for all the systems upgraded). The best system finished in 17 minutes, and the slower ones 45 minutes to an hour. This includes download time of all packages which is relatively quick for me since the connection here is pretty fast.

The thing is, we tend to neglect the time spent tweaking the system the way we want it. I believe I would spend another couple of hours more installing applications, setting up system settings, chosing themes, and so on on each machine.

Be prepared to do new install if upgrade should not work and can't be repaired. So far, that hasn't been necessary.

---

### Post by monkeybrain20122 on 2018-06-21
Clean install any time. It is a no brainer. Upgrade takes a lot longer (a clean install takes 10 minutes)  and if you have many customized configurations it likely fails and leaves you with a broken system, but if your system is pristine (not many customization, third party software, ppa etc) then what have you got to lose with a clean install?

I selectively choose some config files (like .mozilla) I want to keep, backup data and do a clean install, then replace those files after and it is the cleanest way since I know exactly which configurations are old. (a separate /home is good but some junk left over config files in /home can still trip you up unexpectedly)

---

