---
title: "How to install Adobe Reader?"
date: 2007-10-22
forum: General Help
---

### Post by raid517 on 2007-10-22
Hi I uninstalled Adobe reader due to some glitches I was having with it and now I want to reinstall it. However 'acroread' and it's associated plugins are no longer on the repositories. So how do I install Adobe Reader in Ubuntu 6.10?

---

### Post by yjsword on 2007-10-22
Maybe you can download it from the website of Adobe.Adobe Reader  for linux!
Extracting it & executing "./INSTALL"
But i think Evince is better for reading PDF file!

---

### Post by forestpixie on 2007-10-22
acroread are in medibuntu - gives version 8, I assume there's a repo for you

---

### Post by Bablefish on 2007-10-22
Also if you check out the Adobe site you will find a .deb file of Acroread . If you can't I'll send you the link just message me.

---

### Post by FuturePilot on 2007-10-22
Add the Medibuntu repository
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Add the gpg key
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
Then 
```
sudo apt-get install acroread acroread-escript acroread-plugins mozilla-acroread
```

---

### Post by alb@nian on 2007-10-22
Thnx FuturePilot

---

