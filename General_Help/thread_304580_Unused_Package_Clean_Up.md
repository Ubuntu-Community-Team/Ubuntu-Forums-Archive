---
title: "Unused Package Clean Up?"
date: 2006-11-22
forum: General Help
---

### Post by lemonsCC on 2006-11-22
Is there anyway to find all packages that are unused on your computer and remove them?  

Such as if i installed program XYZ and it installed dependencies S, T, and U.  I can sudo apt-get remove XYZ but that does not remove S, T, or U.

---

### Post by David Corrales on 2006-11-22
In Edgy, you can use **sudo apt-get autoremove**

---

### Post by karamba_kid on 2006-11-22
Aptitude will remove the dependencies but since you already installed it with apt-get I would first suggest looking through the dpkg.log files in /var/log/and hopefully that and your memory can help you remember what should be removed. There is also an application called deborphan which may be of some help.  Just be carefull not to remove anything you actaully still need.  I would also backup before doing anything too major.

---

### Post by akudewan on 2006-11-22
Howto use aptitude instead of synaptic (and why): [http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

---

### Post by lemonsCC on 2006-11-22
will try autoremove

i will move to aptitude soon.

---

### Post by chrisccoulson on 2006-11-22
There is also a front end to deborphan called gtkorphan. I've used that for stuff I've installed with apt-get, and I've not had a problem.

---

### Post by Bou on 2006-11-22
> **akudewan said:**
> Howto use aptitude instead of synaptic (and why): [http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

What I have never understood is, why doesn't someone hack synaptic to use aptitude instead of apt-get?

Also, wouldn't it be easy to make synaptic "remember" what packages were installed by the user and which as dependencies, and remove the latter when no other package longer needs them? To give it some deborphan capabilities?

---

### Post by mcduck on 2006-11-22
I use deborphan with a custom filter in Synaptic to list only orphaned packages.

---

