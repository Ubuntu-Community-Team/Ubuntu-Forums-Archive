---
title: "Help with command &quot;dd&quot;"
date: 2006-10-31
forum: General Help
---

### Post by hopbine on 2006-10-31
I know that the command
dd if=/dev/sda of=/dev/sdb bs=1024k 
will copy drive a dot drive b. What I want to do however is copy drive a to multiple dribes.
Ihave tried dd if=/dev/sda of=/dev/sdb of=/dev/sdc bs=1024k. It does not work. Any ideas?

---

### Post by skymt on 2006-10-31
The easy way is to use several commands:```
dd if=/dev/sda of=/dev/sdb bs=1024k
dd if=/dev/sda of=/dev/sdc bs=1024k
```Or, if you want to do it in one command, this may work (I haven't tested it, so any real Unix geeks out there can feel free to correct me):```
dd if=/dev/sda bs=1024k | tee of=/dev/sdb /dev/sdc
```Without an of= argument, dd copies data to stdout. The tee command copies stdin to several files.

---

### Post by hopbine on 2006-10-31
Thanks, I have already tried the first solution - remembering to background the tasks - problem is that after the 3 iteration, disc sda gets too slow. If I try the second suggestion using a "tee" where do I put the "bs=1024k" modifier.

---

### Post by skymt on 2006-10-31
> **hopbine said:**
> Thanks, I have already tried the first solution - remembering to background the tasks - problem is that after the 3 iteration, disc sda gets too slow. If I try the second suggestion using a "tee" where do I put the "bs=1024k" modifier.

Just where I put it: in the dd part, before the "|". If you want to do the copies linearly, use "&&":```
dd if=/dev/sda of=/dev/sdb bs=1024k && dd if=/dev/sda of=/dev/sdc bs=1024k
```

---

