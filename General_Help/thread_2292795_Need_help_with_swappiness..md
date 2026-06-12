---
title: "Need help with swappiness."
date: 2015-08-31
forum: General Help
---

### Post by bob146 on 2015-08-31
Thinking of using an old dell I have laying around and I came upon this part about swappiness and ran this command on my computer
```
cat /etc/fstab
```
thats when i noticed this
[HTML]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=9e23f29e-68eb-4749-8070-b4acf27b063d /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=14fa6f70-54f2-4f0b-9e54-7705ed13450c /boot           ext4    defaults        0       2
# /home was on /dev/sdb6 during installation
UUID=73b7f0f0-4e3c-493d-a0b6-0d8e65ed5200 /home           ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=303a0661-3ebd-4ccd-a84d-7a371a8172cf none            swap    sw              0       0
[/HTML]
please tell me what I am looking here that needs to be remounted? I'm new to linux and trying to learn.

---

### Post by claydoh on 2015-08-31
> **bob146 said:**
> pardon me for interrupting here but i was reading this thread and thinking of using an old dell I have laying around and I came upon this part about swappiness and ran this command on my computer
```
cat /etc/fstab
```
thats when i noticed this
[HTML]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb5 during installation
UUID=9e23f29e-68eb-4749-8070-b4acf27b063d /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=14fa6f70-54f2-4f0b-9e54-7705ed13450c /boot           ext4    defaults        0       2
# /home was on /dev/sdb6 during installation
UUID=73b7f0f0-4e3c-493d-a0b6-0d8e65ed5200 /home           ext4    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=303a0661-3ebd-4ccd-a84d-7a371a8172cf none            swap    sw              0       0
[/HTML]
please tell me what I am looking here that needs to be remounted? I'm new to linux and trying to learn  and again Pardon my intrusion here.

What is wrong? your fstab is fine -- the part that mentions "errors" is simply a mount option to take if there is a problem.

But you really should ask this question as a new thread, else only a very few people will see it here.

---

### Post by Bucky Ball on 2015-08-31
*Post moved to own thread.*

---

### Post by mörgæs on 2015-08-31
Here's a brief guide on [swappiness]("http://ubuntuforums.org/showthread.php?t=2130640&p=12580289&viewfull=1#post12580289") and other tricks. I hope it helps.

---

