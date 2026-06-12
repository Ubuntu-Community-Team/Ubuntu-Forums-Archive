---
title: "Upgrading between LTS releases"
date: 2016-05-10
forum: General Help
---

### Post by checoimg on 2016-05-10
I want to follow this [instructions]("http://askubuntu.com/questions/769815/why-does-do-release-upgrade-try-to-upgrade-my-system-to-15-10-and-how-to-i-make/769835#769835") from AskUbuntu. But I wonder if I could just be asking for trouble, by doing this. Should I just make fresh installs ?

Thank you

```
[COLOR=#111111][FONT=Ubuntu]Before doing the [/FONT][/COLOR]sudo do-release-upgrade -d[COLOR=#111111][FONT=Ubuntu], make sure that your [/FONT][/COLOR]/etc/update-manager/release-upgrades[COLOR=#111111][FONT=Ubuntu] file ends in [/FONT][/COLOR]Prompt=lts[COLOR=#111111][FONT=Ubuntu]. This will enable the upgrade tool to fetch the next LTS release (16.04) instead of just the next release (15.10).[/FONT][/COLOR]
``` by Organic Marble

---

### Post by QDR06VV9 on 2016-05-10
As any old timer would suggest a fresh or new install is always best.
But that said i upgrade all the time but I remove proprietary(Non Free Video) drivers before doing so ..and your mileage still may vary.
EDIT: I forgot to say I also disable all PPA's that I have added.
If 14.04 is working good for you now as is...why upgrade?  
Kind Reegards

---

### Post by Mark Phelps on 2016-05-10
I normally do not UPGRADE from one Ubuntu release to the next, but prefer to do a clean-install each time.

That said, when the upgrade tool offered an upgrade from 15.10 to 16.04 this time, I decided to try it and see how it goes.

All-in-all, it went well -- at least, it did not introduce any serious problems.

However, it did not upgrade nearly all the software that I had installed through Synaptic -- which was a surprise, as I thought it would.  I ended up redownloading and reinstalling nearly all of the apps.

I also discovered, that the age-old UTC "fix" does not work in 16.04, so I had to do some digging to find the new solution -- as I dual-boot with Windows and want ALL the OSs to show the same local time.

Good Luck

---

### Post by SeijiSensei on 2016-05-10
> **Mark Phelps said:**
> I also discovered, that the age-old UTC "fix" does not work in 16.04, so I had to do some digging to find the new solution -- as I dual-boot with Windows and want ALL the OSs to show the same local time.
Can you point me to that "fix" for 14.04?  I'm really tired of having to reset my clock every time I switch operating systems in a dual-boot environment.

---

### Post by QDR06VV9 on 2016-05-10
> **SeijiSensei said:**
> Can you point me to that "fix" for 14.04?  I'm really tired of having to reset my clock every time I switch operating systems in a dual-boot environment.

Have you seen this yet? [http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html](http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html) 
And it was also said to work with ubuntu 16.04 also.
Regards

---

### Post by checoimg on 2016-05-10
Totally agree with the "Why upgrade?", But in the case of deciding to upgrade I wonder if there's a way to reduce download requirements. What about a mixture of holding/disabling/upgrading ? Has anyone tried such an option ?

Specifically Holding all applications that are important (Why upgrade?), Disabling but keep PPA's (Upgrades are slow there), Upgrade to try to keep your system but also get the latest Kernel and DE improvements. **Without Ubuntu MAKE**

---

### Post by Bucky Ball on 2016-05-10
Before upgrading, if you go that way, apart from disabling third-party (manually installed) PPAs and vid drivers, as suggested, also run these commands:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade 
```

Make sure your machine is fully up-to-date before running the upgrade -d command to upgrade to the next LTS. Good luck.

---

### Post by checoimg on 2016-05-10
So HOLD all App's including PPA's and then autoremove/update/upgrade/dist-upgrade ? Thanks :D Do I still have to wait for **16.04.1** ?

---

### Post by Bucky Ball on 2016-05-10
The upgrade will appear as an option in the regular way (Software and Updates etc.) at the point release, yes, but you can do it via a terminal at any time.

Goes without saying and sure you've already done it, but back up any valuable data before proceeding. You may even want to clone your current / partition. ;)

Good luck.

---

### Post by checoimg on 2016-05-10
Yep :D Thank you all

---

### Post by Bucky Ball on 2016-05-10
Please mark as solved if you're happy your original question has been answered. This will not close the thread to further discussion. ;)

---

### Post by SeijiSensei on 2016-05-10
> **runrickus said:**
> Have you seen this yet? [http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html](http://www.webupd8.org/2014/09/dual-boot-fix-time-differences-between.html) 
And it was also said to work with ubuntu 16.04 also.
Regards

Thanks!  I'll give it a try in the morning.  Having to edit the Windows registry to do this is a bit of a pain though.  (I'd prefer to keep the hardware clock on UTC and force Windows to compensate.)

---

### Post by grahammechanical on 2016-05-10
Err, I am sorry to say this, but there is something that has been missed. The command that the OP was asking about contained this:

> do-release-upgrade -d

The -d switch will not upgrade 14.04 or 15.10 to 16.04 but to the Yakkerty Yak development branch of 16.10. The "d" in "-d" = development. So, the correct answer is "Don't do it."

I have nothing against Yakkerty Yak. I am using it myself, daily. It is stable. But 16.10 will only have 9 months support from when it is released (October) and a person should not be running the development branch if they are not willing & prepared for something to break in the coming weeks & months. If a person really does want to test Yakkerty Yak then the way to get it is to install a daily ISO image. Using that command even from 16.04 may not be successful becaus ethere are now big code differences between 16.04 & 16.10.

Regards.


Regards.

---

