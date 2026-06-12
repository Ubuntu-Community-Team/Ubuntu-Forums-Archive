---
title: "How to restore or reinstall lubuntu 12.04 on a dual boot (XP) machine?"
date: 2014-10-15
forum: General Help
---

### Post by Mark_M. on 2014-10-15
Hi there,

I have a dual boot machine (XP/lubuntu 12.0.4) that I use from time to time for various number-crunching applications. I'd like to restore the lubuntu portion (particularly the python installation) to its initial state either through a 'restore' process (if one exists), by re-installing lubuntu 12.0.4 or by installing 14.04. As you might guess, I want any installation to be on the same partition on which lubuntu is currently installed -- and I'd like to avoid doing anything to the XP installation.

I've created a 12.04 live CD but i didn't want to go too far down the prompts without understanding what I should be doing either to restore the original installation or overwrite the **correct** partition and load a fresh install.

As alluded to above, how would I select the correct partition (partition size? some other attribute?)

Any advice would be helpful.

Also, is there much difference in terms of system requirements between lubuntu 12.04 and lubuntu 14.04? I quite like the 12.04 but would consider moving on to 14.04 if it is similarly light.

Thanks in advance for all feedback.

---

### Post by Mark Phelps on 2014-10-15
Sorry, but there is no "system restore" function in Ubuntu.  To go back to what you had initially, just after the install, you would have to erase what you have and do a clean installation.  

IF you do that, make sure you do NOT choose the "Reinstall" option -- as that actually erases THE ENTIRE DISK! That option is very poorly worded in the installer, and reads like it will only erase Ubuntu, but in fact, removes ALL the partitions, reformats the entire drive, and reinstalls from scratch.

IF you can, it would be safer if you could do an image backup of XP to an external drive using Macrium Reflect (Windows backup/restore app) PRIOR to erasing and installing Ubuntu.

---

### Post by grahammechanical on 2014-10-15
You have to decide what you are going to do. One or the other. If you decide to move on to Lubuntu 14.04 then you can upgrade. How to do that here.

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Do back up your data.

Are you aware that Lubuntu 12.04 only has/had support for 18 month?. Whereas, Lubuntu 14.04 has support for 3 years? 

> [COLOR=#666666][FONT=Ubuntu]Unlike Ubuntu, Lubuntu 12.04 is not a LTS, this version will be supported for 18 months.[/FONT][/COLOR]

[http://lubuntu.net/blog/lubuntu-1204-now-available](http://lubuntu.net/blog/lubuntu-1204-now-available)

> **We are happy to announce that Lubuntu 14.04 has LTS Support (3 years)**

See, the first link.

Regards.

---

### Post by Mark_M. on 2014-10-15
Thanks to both of you for providing some answers.

I'm thinking upgrade is the path of least resistance here (and worth a try -- since a re-install will overwrite the partition anyway). Does 

```
sudo do-release upgrade
```

give me a fresh python (i.e. blow away anything I've installed)? And if so, what version of python will I have in 14.04?

---

### Post by radwanski-michal-a on 2014-10-15
No. Do release upgrade will try keep your applications untouched. I think the best way is to reinstall.

---

