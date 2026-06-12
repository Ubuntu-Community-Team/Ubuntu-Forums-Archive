---
title: "How to get rid of Automatix2 for 6.10"
date: 2006-12-07
forum: General Help
---

### Post by Roasted on 2006-12-07
Little problem here. I tried to get Automatix2 for my brother's linux machine so he could get the flash 9 beta installed. However I accidently downloaded 6.10 version. Okay, no big deal, right? Wrong. I uninstalled it in terminal and synaptic package manager. I also ran the purge command in terminal. Now everytime I install Automatix2 for 6.06, it STILL installs at 6.10. What in the hell?

---

### Post by aidanr on 2006-12-07
how bout trying "package -> force version" in synaptic, or "right click -> mark for complete removal"

oh of course also make sure you have the dapper repository in /etc/apt/sources.list instead of the edgy repository

i think it should be

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

---

### Post by Roasted on 2006-12-07
I did do complete removal in synaptic, didn't work.

I'll try the other things tomorrow when I have access to the computer again.

---

### Post by taurus on 2006-12-07
```
sudo aptitude remove automatix2
```
Then, edit your /etc/apt/sources.list and change it from edgy to dapper...

```
gksudo gedit /etc/apt/sources.list
```
```

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

```
Then,
```
sudo aptitude update
sudo aptitude install automatix2
```

---

### Post by strabes on 2006-12-07
yeah the problem was that you still had the edgy source in there. You can install the flash 9 beta manually by downloading it from [here](http://labs.adobe.com/technologies/flashplayer9/) and putting it in your /usr/lib/firefox/plugins folder.

---

### Post by Roasted on 2006-12-08
> **strabes said:**
> yeah the problem was that you still had the edgy source in there. You can install the flash 9 beta manually by downloading it from [here](http://labs.adobe.com/technologies/flashplayer9/) and putting it in your /usr/lib/firefox/plugins folder.

Tried that on my machine, did everything right, exact to the directions... didn't work. I got Automatix2 and it worked fine. Some folks around here spoke about a bug or some kind of common problem which is why my manual installation didn't work. *shrug*

---

