---
title: "major update for Ubuntu 14.04.2"
date: 2018-01-07
forum: General Help
---

### Post by okkie2 on 2018-01-07
Yesterday afternoon while doing sound conversion with Audatious a grey screen appeared notifying me of "major update for Ubuntu 14.04.2". Computer started working by rebooting and iassumed this will be a long story so I left and went to bed. This morning it was still on the backup screen but nothing happening till now, Sunday evening.

Does anyone know about this ? does it mean a complete reinstallation ?


Thanks

---

### Post by TheFu on 2018-01-07
Support for 14.04.2 ended in 2016. [https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life)
Move to 14.04.5 if you want support.

This should do the upgrade, but it might just go from .2 --> .3. Then do it again, if needed and again. ;)
```
$ sudo apt update && sudo apt dist-upgrade
```

I'm a .1 release guy.  14.04.1 support is for the full expected period.  .2, .3, .4 are intermediate versions that only have 6-9 months of support.  The .5 version finishes out the support period for the LTS. Information is power.

---

### Post by Impavidus on 2018-01-07
Moving to 14.04.5 just means installing all regular upgrades and the HWE stack for 14.04.5. [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I don't know about a "major update" though. To me, Ubuntu always talks about upgrades without specifying whether they're minor or major.

---

### Post by okkie2 on 2018-01-08
Sorry, the word is 'Sheduled" update. I just again got two quick short messages in a row like yesterday  " scheduled update delayed". I can however hear the machine is working, but it is already more than two days. The messages appear on the right side of the screen , two small blocks in succession "scheduled update delayed".
 Shall I just wait or is there something I can do ?
Thanks

---

### Post by okkie2 on 2018-01-08
Thanks a lot for the info. I accept then that once new LTS is installed, you leave it as is and just do the normal improvements as they come around. Hope I have another Five years.  Enjoy

---

### Post by Impavidus on 2018-01-08
So, if I get this right, you can use your computer, but something seems wromg with the upgrades?

Try to run```
sudo apt-get update
sudo apt-get dist-upgrade
```and report the output. Maybe we get a useful error message.

---

