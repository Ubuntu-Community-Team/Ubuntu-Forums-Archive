---
title: "how often to fsck?"
date: 2008-07-03
forum: General Help
---

### Post by hyper_ch on 2008-07-03
By default, Ubuntu will set each partition to fsck after x reboots or rather x mountings... however I've wondered now if that is necessary? How does it calculate x (it seems to be different for each partition)...

How often should you do it? Why should you do it?

---

### Post by Anzan on 2008-07-03
man fsck

I see no reason to fiddle with the settings.

---

### Post by confused57 on 2008-07-03
This may explain why you need to do a file system check:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_checks_on_bootup](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_checks_on_bootup)

---

### Post by hyper_ch on 2008-07-03
it doesn't really explain it... I mean I can understand after an improper shutdown to do a check by why every 30 boots or so?

---

### Post by Anzan on 2008-07-03
Juuuuuust in case.

---

### Post by brian_p on 2008-07-03
> **hyper_ch said:**
> By default, Ubuntu will set each partition to fsck after x reboots or rather x mountings... however I've wondered now if that is necessary? How does it calculate x (it seems to be different for each partition)...

How often should you do it? Why should you do it?

An ext3 file system doesn't absolutely require an fsck even after an unclean shutdown, so in that sense setting it to check after x mounts is unnecessary. But a read of the -c option in man tune2fs might cause you to change your mind.

```
sudo dumpe2fs -h /dev/hdaN
```

gives information for a partition. tune2fs lets you alter the frequncy of checking.

---

### Post by brian_p on 2008-07-03
> **hyper_ch said:**
> it doesn't really explain it... I mean I can understand after an improper shutdown to do a check by why every 30 boots or so?

30 is in the interval 20 to 40 which is coded into mk2fs and chosen in a mildly random manner so that not all file systems are checked at the same time. There appears to be nothing magical about 20 to 40; it is, I imagine, picked as being a reasonable interval.

To repeat: fsck does not need to be run on an ext3 file system after a dirty closedown.

---

### Post by sujoy on 2008-07-03
i have fsck enabled on boot only on my /

---

### Post by dentaku65 on 2008-07-03
I think that fsck happens every 30 reboots/boots
You can force fsck to the next reboot doing:

```
cd /
```
```
sudo touch /forcefsck
```

Then, on the next reboot, fsck will be executed

I needed once because on my old hd I was earing strange rumors of the hd headers...

---

### Post by Pjotr123 on 2008-07-03
I've set it at once every 100 boots.

More than enough. The 30 is irritating for desktop users. More fit for servers that almost never reboot.

This is how to influence it:
[http://ubuntutip.googlepages.com/tipsandtweaks](http://ubuntutip.googlepages.com/tipsandtweaks)
(number 3 )

---

