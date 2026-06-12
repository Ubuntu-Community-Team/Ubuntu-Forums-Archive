---
title: "save apt-get information in text"
date: 2007-08-07
forum: General Help
---

### Post by TorchlightJay on 2007-08-07
So I am running a Feisty install in text mode and something has gone corrupt. Now I want to reinstall but I don't want to have to try and remember everything I need to install. How do I save all of my download information from apt-get in text mode?

---

### Post by ayoli on 2007-08-07
this can do the trick:
```
dpkg -l | grep '^ii' | awk '{print $2}' > packages-list.txt
```
that will list all installed packages in a text file, and to reinstall you can do:
```
for i in `cat packages-list.txt`; do apt-get install $i; done;
```

---

### Post by TorchlightJay on 2007-08-07
YO dude, thanks for the info.

---

### Post by hlevine@leonora.co.za on 2008-06-16
Hi
I also reload all the time.  How do I reuse the packages I have already downloaded.  Can I just copy them into the /var/cache/apt/archives?
I play around with a lot of packages.
Regards

---

### Post by Keith Hedger on 2008-06-16
From synaptic File->Add Downloaded Packages and select a folder with any downloaded debs you've saved and synaptic will install them

---

