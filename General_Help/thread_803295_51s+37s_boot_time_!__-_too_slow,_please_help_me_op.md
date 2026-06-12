---
title: "51s+37s boot time !  - too slow, please help me optimize"
date: 2008-05-22
forum: General Help
---

### Post by Andre-D on 2008-05-22
Travelmate 4233 ,Core 2 Duo T5500  ,1GB RAM

Ubuntu installed on HD.
from I select kernel (press a key) in GRUB - till unsername box appears, it takes 51 sec.
Then, after entering username+password, till gname-panels are ready: 37 seconds.

all together, almost 1 minute 30 sec. , more is Bios/POST is inclused.

---

### Post by chrisccoulson on 2008-05-22
Could you please install bootchart and post the results here (they will get stored in /var/log/bootchart)
```
sudo apt-get install bootchart
```

---

### Post by kkkkdddd on 2008-05-22
If you are the only person who uses this computer, you could try enabling auto login.
Go to System->Administration->Login screen->Security
Enable auto login and choose user.

---

### Post by chrisccoulson on 2008-05-22
That won't speed up the boot time though.

Thinking about it, 51s to GDM isn't that bad (depending on your hardware), although it isn't great. The 37s after log in isn't really normal though (although I've noticed my panels take quite a long time to appear in Hardy, but not 37s)

---

### Post by Andre-D on 2008-05-22
please see attached "log"-image...

I see irony in this: Ubuntu,/Linux , nice clean OS that uses less RAM, takes much longer time to boot than a pile of bloatware takes to fill computer's memory (windows).

It must be a huge possibility for improvement here...

---

### Post by chrisccoulson on 2008-05-22
Your boot time really doesn't look that bad, although I can't see when gdmgreeter starts as your boothart finishes before then, so it could take a bit longer than shown here I suppose.

You might be able to profile your boot in order to shave some time off what it takes readahead to read in all the files. To profile your boot, please have a look here: [http://ubuntuforums.org/showthread.php?t=254263]("http://ubuntuforums.org/showthread.php?t=254263")

---

### Post by Andre-D on 2008-05-22
In fact, I already profiled my boot time using that article. (it saved me only 2 seconds) - and it was done before I started this thread.

The "bonus hack" seems to be applied by the distro already.

Does anybody know if there is any work being done in order to optimize Linux boot-time ? I do not mean to bitch - but such neat OS with small memory consumtion, should be able to load twice as fast as windows do.

---

### Post by Andre-D on 2008-05-26
Why is the disk performance so slow ? peaking at 20MB/s is that normal ?

My disk seems to perform better than that...
> andre@Ubuntu:~$ sudo hdparm  -t /dev/sda

/dev/sda:
 Timing buffered disk reads:  102 MB in  3.05 seconds =  33.41 MB/sec


---

### Post by K.Mandla on 2008-06-01
Sorry if this is self-serving or tacky, but ... 

[http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/](http://kmandla.wordpress.com/2008/05/04/howto-set-up-hardy-for-speed/)

---

