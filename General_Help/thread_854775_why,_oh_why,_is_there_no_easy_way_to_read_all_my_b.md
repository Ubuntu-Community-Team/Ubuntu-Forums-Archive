---
title: "why, oh why, is there no easy way to read all my boot messages?!?!"
date: 2008-07-09
forum: General Help
---

### Post by moore.bryan on 2008-07-09
sounds like it should be simple, but it is so far from it. 

[LIST=1]
[*]let me tell you i've checked EVERY file in /var/log and NONE of them contain ALL the messages printed on the screen during startup.
[*]i've enable bootlogging and the /var/log/boot file still tells me nothing is logged.
[*]"dmesg | less" tells me absolutely nothing.
[/LIST]
now, short of taking a photo of the screen during startup, how in the world can i read its output?
:(

---

### Post by iaculallad on 2008-07-09
For Gutsy and Hardy?: Instead of opening **/var/log/boot** file to view the boot process, Open **/var/log/messages** file.

```
cat /var/log/messages
gedit /var/log/messages
```

---

### Post by moore.bryan on 2008-07-09
yeah, tried that one... still does not contain all the messages, specifically these two:
```
exec 34: env: not found
```
and
```
cannot open font file lat0-sun16
```

---

### Post by iaculallad on 2008-07-09
Had you tried listing the /var/log on Gutsy/Hardy?, you could see that boot logging message files are tarred/backup'ed. Try extracting the files and locate your specific error messages/codes.

i.e: messages.x.gz

---

### Post by VMC on 2008-07-09
This has come up before many times. Since you labeled it [all variants], it is possible, using previous versions, but not using Harty. I installed it, but it just doesn't work. I traced the reasons and it has something to do with the kernel conflicts.

---

### Post by moore.bryan on 2008-07-09
unfortunately, yes. the error lines have just appeared in the last two or three boots tonight, so the backup logs are somewhat useless, but i checked them any way.

---

### Post by moore.bryan on 2008-07-09
> **VMC said:**
> This has come up before many times. Since you labeled it [all variants], it is possible, using previous versions, but not using Harty. I installed it, but it just doesn't work. I traced the reasons and it has something to do with the kernel conflicts.
then the REAL question is why no one has enabled a logging of those first messages...

EDIT:
just for the record, i've solved both of the error messages, but my initial irritation at not having a COMPLETE log of the startup messages has not abated.
;-)

---

### Post by VMC on 2008-07-09
Here's some of the reasoning behind it(upstart). You can read the bug report in launchpad here:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120)

---

### Post by moore.bryan on 2008-07-09
> **VMC said:**
> Here's some of the reasoning behind it(upstart). You can read the bug report in launchpad here:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/94120)
thanks for the link... interesting and even more irritating that this has been a "problem" for so long and no solutions have been released.

---

