---
title: "how often should i sudo apt-get autoremove?"
date: 2018-06-19
forum: General Help
---

### Post by ardouronerous on 2018-06-19
Recently, I did an sudo apt-get autoremove on my laptop, which has a 120GB SSD.
Before I executed the command, the free space on my laptop was 93GB, but after I did the command, free space became 98GB.

How often should I do this?

---

### Post by #&amp;thj^% on 2018-06-19
As often as you want>>>No harm in a weekly "autoremmove" in fact it is a good practice. :)
Just keep an eye on whats being removed and if any questions just post in the forums for peace of mind. ;)

---

### Post by ardouronerous on 2018-06-19
Okay, thanks :)

---

### Post by warmango on 2018-06-19
About every other week. What it does is clear cache files that may still linger after running APT commands. And I think it removes plugins (libfiles) that arnt used by software that is currently installed.

---

### Post by Holger_Gehrke on 2018-06-19
> **warmango said:**
> About every other week. What it does is clear cache files that may still linger after running APT commands. And I think it removes plugins (libfiles) that arnt used by software that is currently installed.

Um, NO. 'apt clean' and 'apt autoclean' remove the cache (the latter only the files which can't be downloaded from the server any more because they are outdated). 'apt autoremove' removes packages which were installed as dependencies for other programs and were not removed when the program that depended on them was removed. This regularly happens to kernel-images, because there's an almost empty package which depends on the current kernel (and I think the previous one). Whenever that package gets updated, a new kernel is downloaded as dependency of the package and an old kernel stops being depended on and will get removed the next time you run 'apt autoremove'. To check in advance what would get deleted you can add the option '-s' or the long option '--dry-run' to 'apt autoremove'.

Holger

---

### Post by Habitual on 2018-06-19
I do mine first Thursday of every month, after 3 Thursdays of
```
apt-get update && apt-get dist-upgrade -yqq
```

YMMV

---

### Post by cruzer001 on 2018-06-19
There are also other options that you may find useful.

Synaptic Package Manager will notify you if there are any packages to autoremove.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

BleachBit also has autoremove built in and it will clean other crud that could be in your system.  An example would be extra language packs that can add up to a gig or more.  Just be careful how you set it up.

[https://www.bleachbit.org/features](https://www.bleachbit.org/features)

```
sudo apt install bleachbit
```

---

