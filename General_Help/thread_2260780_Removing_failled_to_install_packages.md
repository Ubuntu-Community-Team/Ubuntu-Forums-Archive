---
title: "Removing failled to install packages"
date: 2015-01-14
forum: General Help
---

### Post by Stevenukas on 2015-01-14
Hi, tried to install teamviewer 64bit, later on I have found out I can only have 32bit, its obvious that sudo apt-get remove should remove it, but it removes the properly working version, not the 64 which is giving me errors once in a while. 
 [ATTACH=CONFIG]259227[/ATTACH]

---

### Post by Bucky Ball on 2015-01-14
*Thread moved to **General Help**.*

What computer are you using? Is it 64bit or 32bit? You are saying you have a 32bit version of Ubuntu? Which release are you using? Have you tried to remove it using Software Centre? That might show you both versions and you can select which to remove.

Perhaps you could remove the working version, then remove the not working version of Teamviewer, then install the one that works for you, the 32bit version. An idea ... ;)

---

### Post by Stevenukas on 2015-01-14
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

What computer are you using? Is it 64bit or 32bit? You are saying you have a 32bit version of Ubuntu? Which release are you using? Have you tried to remove it using Software Centre? That might show you both versions and you can select which to remove.

Perhaps you could remove the working version, then remove the not working version of Teamviewer, then install the one that works for you, the 32bit version. An idea ... ;)

I have 64 bit Ubuntu, tried removing 32bit version TV and the apt-get remove teamviewer and this is what I get:
```

Reading state information... Done
Package 'teamviewer:i386' is not installed, so not removed

```

Thank you

---

### Post by whitesmith on 2015-01-14
Looks like the above package is removed. As Bucky Ball said, try the Software Center to see what's installed if anything.

---

### Post by Stevenukas on 2015-01-14
> **whitesmith said:**
> Looks like the above package is removed. As Bucky Ball said, try the Software Center to see what's installed if anything.

as the terminal says, there are no tv installed, same thing shows on the software center. 

[ATTACH=CONFIG]259231[/ATTACH]

---

### Post by Stevenukas on 2015-01-14
Whats more strange, I have cleaned up my system with Synaptic Application Manager,removed old files or not installed, used [this]("http://sites.google.com/site/easylinuxtipsproject/clean") link to clean up my system, not its working, at least for now. But Ubuntu Software Center still doesnt see teamviewer :([ATTACH=CONFIG]259232[/ATTACH]

---

