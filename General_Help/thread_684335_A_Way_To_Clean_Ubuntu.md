---
title: "A Way To Clean Ubuntu?"
date: 2008-02-01
forum: General Help
---

### Post by FrankBro on 2008-02-01
Ok, so ive runned ubuntu on my laptop for a couple of months. Since it was my first time with ubuntu, i tryed a lot of stuff ( installed a lot of packages ). Now my question is, is there a way to make a clean to lets say fresh install ? To when i had it installed with the live cd ? Thx

---

### Post by jrusso2 on 2008-02-01
Do a reinstall?  I don't know what the problem is did you mess something up?  Linux doesn't have a registry to clean.

---

### Post by faulkes on 2008-02-01
> **FrankBro said:**
> Ok, so ive runned ubuntu on my laptop for a couple of months. Since it was my first time with ubuntu, i tryed a lot of stuff ( installed a lot of packages ). Now my question is, is there a way to make a clean to lets say fresh install ? To when i had it installed with the live cd ? Thx

If you have installed packages and then later removed them because you didn't like them, then there are likely cached files that can be removed.

From the apt-get manpage:

> autoclean
           Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.


So you can run the following command (as well as it being safe to run):

```
sudo apt-get autoclean
```

You may wish to also look at the autoremove option in the manpage as well.

Faulkes

---

### Post by FrankBro on 2008-02-01
nah what i mean is, i installed so much stuff that i want to remove everything and get ubuntu back to what it was at the begining. Im too lazy to uninstall 1 by 1.

---

### Post by Rocket2DMn on 2008-02-01
> **FrankBro said:**
> nah what i mean is, i installed so much stuff that i want to remove everything and get ubuntu back to what it was at the begining. Im too lazy to uninstall 1 by 1.

Then a full reinstall is what you're looking for.  There is no utility to just restore the initial setup.

---

### Post by oldos2er on 2008-02-01
> **FrankBro said:**
> nah what i mean is, i installed so much stuff that i want to remove everything and get ubuntu back to what it was at the begining. Im too lazy to uninstall 1 by 1.

 You don't need to uninstall them one-by-one, you can write a sudo apt-get remove command a mile long if you wish.
 Or go into Synaptic and mark all the packages you want to remove.

---

### Post by HermanAB on 2008-02-01
Re-install.  It only takes about 30 minutes and then you have all the latest stuff.  If your /home is a separate partition, then don't format it and you will keep all your data and settings.

---

### Post by bodhi.zazen on 2008-02-01
To clean see these links :

Clean/Degunk:

 [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

If you want a clean install, do a clean install. If you want to remove packages, use synaptic or 

```
sudo apt-get remove --purge <package-list>
```

What package are we talking about, what are you trying to remove / clean exactly ?

---

### Post by FrankBro on 2008-02-02
i tryed installing stuff to record music and i ended up with a **** load of little apps i didnt want + new options in grub. I just wanna like purge everything except ubuntu itself, and then install what i need back.

---

### Post by dcstar on 2008-02-02
> **FrankBro said:**
> i tryed installing stuff to record music and i ended up with a **** load of little apps i didnt want + new options in grub. I just wanna like purge everything except ubuntu itself, and then install what i need back.

It would be quicker doing a fresh install - if you have a separate /home partition then this becomes a lot easier as all your user data is preserved if you blow away the original Ubuntu "/" partition.

---

