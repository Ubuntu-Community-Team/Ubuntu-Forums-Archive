---
title: "Boot up time on my laptop is really slow"
date: 2007-05-13
forum: General Help
---

### Post by ekb on 2007-05-13
My laptop takes approximately 2 mins to boot up. From my observation, the longest process was checking file system on sda1. Is it because I have a dual boot with winXP? I've installed bootchart to get the visualised log of boot up however, I have no idea on how to read it so I attached it along with this thread. May anyone suggest me what process take longest during booting? Also please suggest any possible solutions on how to speed up the boot time.

I appreciate any helps. Thank you.

---

### Post by Ken_Lewis81 on 2007-05-14
The line is fsck.vfat which takes the most time/resources.  Ubuntu won't continue until that drive has been checked and mounted.  I can't say why your drive needs checking **every** boot -- is there anything in the logs (/var/log/syslog and via the 'dmesg' command) which talk of it being unmounted badly when you shut down?

You can, of course, disable fsck checking for the drive to skip this.  I wouldn't advise it, because if there's something really wrong with your files, it wouldn't be wise to compound the issue and mess them all up.  Googling finds me this ubuntuforums thread: [http://ubuntuforums.org/showthread.php?t=359154](http://ubuntuforums.org/showthread.php?t=359154) where someone experiencing something similar has their issue resolved by removing a 0-byte, 0-sector file that's somehow there.  I suggest that you run sudo "fsck.vfat -w -a /dev/*partition*" for your FAT partition when you're in Ubuntu to resolve any mess in your filesystem.

Hope that helps.
Take care.
Ken.

---

### Post by ekb on 2007-05-14
Thank you very much for your suggestion. I'll try it first thing after I'm able to boot my Ubuntu properly.
I somehow messed with GRUB. The whole story is here: [http://ubuntuforums.org/showthread.php?p=2651622#post2651622]("http://ubuntuforums.org/showthread.php?p=2651622#post2651622")

---

### Post by ekb on 2007-05-14
Sorry. Still no luck with it. When I run
```
sudo fsck.vfat -w -a /dev/sda#
```

It didn't produce any output. Also, the boot up time still takes approximately 2 mins after running the code. Am I doing something wrong here? :confused: 

Please suggest any other possible solutions to help fix this problem 

Thank you.

---

### Post by hessiess on 2007-05-14
2 mins isant bad, xp takes 10 munites to boot on my computer, 1 min for ubuntu. try putting your stuff on a separate partition, seems to be slower when there are more files in the main partition

---

### Post by ekb on 2007-05-14
My XP takes less than a minute to get to log in screen (although, another 1 min after log in). The problem is, the first partition (sda1) is my recovery partition (it comes with laptop) so I don't think it's a good idea to play around with it.

Thanks for your suggestion anyway. :)

---

### Post by ekb on 2007-05-15
I've already fixed all the files that caused the errors (some of the files' names aren't in English). However, Ubuntu still checks fat partition every time it boots. This doesn't happen to my ntfs partition though. Is there anyway to specifically tell the system that it only needs to check the particular partition for, says, once in ten bootups? I don't think the fat partitions are that important to be checked every time anyway since it only has windows in it hence skipping the check won't cause any problem. Is my reasoning correct here?

Thank you.

---

### Post by Enverex on 2007-05-15
> **hessiess said:**
> 2 mins isant bad, xp takes 10 munites to boot on my computer

Something is either very wrong with your Windows install or very wrong with your hardware...

---

### Post by hessiess on 2007-05-16
> **Enverex said:**
> Something is either very wrong with your Windows install or very wrong with your hardware...


i alwase get replys like that when i say it takes 10 munites to boot!. what i meen is it takes 10 munites to become usable, it boots in 2 munites

---

### Post by Enverex on 2007-05-16
> **hessiess said:**
> i alwase get replys like that when i say it takes 10 munites to boot!. what i meen is it takes 10 munites to become usable, it boots in 2 munites

In that case try not filling it with spyware and having every app you ever install set to start on login. The amount of times I hear about people complaining about Windows speed and they have like 200 processes running on boot and so many icons by the system clock that it stretches half way across the screen.

---

