---
title: "Movies ( Games with wine ) Even google earth with out wine still flashs..."
date: 2008-05-10
forum: General Help
---

### Post by Cpuboye11 on 2008-05-10
Hi, 

This problem i have been having is all the way from 7.10.. And After a clean install to 8.0x.

Everything is fine- in firefox or anything else that you can easily install from the Add And Remove... Things like Warcraft III and other games- also including Google Earth- installed from this-

```
 Re: Google Earth on Ubuntu 8.04
This way will work with only a few commands. ;]
You need the medibuntu repo. I will supply howto in one min bear with me ;]

step one: copy paste this command
Code:

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

step two: copy paste this command
Code:

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

step three: copy paste this command
Code:

sudo apt-get install googleearth-4.3

when installed just press alt+f2 and type googleearth or find it under internet in the menu

enjoy!
```

Flashes when ever you hit a mouse key...

Not when you move the mouse when you hit a button. Such as you clicking on something with in the window. The whole thing flashes.... I'm not sure where to begin or what else to tell you, because i have no idea.

If you need any infor. Please ask, because i wish this would stop....

Thanks,
Kyle

---

### Post by Cpuboye11 on 2008-05-11
Hmmm.. any ideas??? 


This is the only problem I have- and I don't understand what it is doing... All my visual effects within Ubuntu work great. With Advanced Desktop Effects program. 

So please any ideas would be helpful :-D

---

### Post by Cpuboye11 on 2008-05-14
The problem seems to be connected to Compiz and MetaCity....


When i switch back to meta... it runs with out the flashes.. or white blinks..

When in compiz, it flashes and blinks...

Is there any way to get it working in Compiz????

---

### Post by Cpuboye11 on 2008-05-14
Is this because my graphics card- Ati 7500m is black listed or w/e?

---

### Post by Cpuboye11 on 2008-05-17
<-- Bump -->

---

### Post by Gunman1982 on 2008-05-17
> **Cpuboye11 said:**
> The problem seems to be connected to Compiz and MetaCity....

yup thats the problem, the ATI/AMD fglrx driver can't handle compiz in combination with other 3d applications. It isn't even restricted to google earth.

> **Cpuboye11 said:**
> 
Is there any way to get it working in Compiz????
Sadly not yet. You have to either switch to metacity  for 3d applications and even for some java applications or deactivate compiz completely.

---

### Post by Cpuboye11 on 2008-05-18
> **Gunman1982 said:**
> yup thats the problem, the ATI/AMD fglrx driver can't handle compiz in combination with other 3d applications. It isn't even restricted to google earth.


Sadly not yet. You have to either switch to metacity  for 3d applications and even for some java applications or deactivate compiz completely.



:(((((


Will they ever try and fix the problem... Or is it just black listed.... ( Forever...)

---

### Post by Gunman1982 on 2008-05-18
I guess future versions of the ati driver or xorg2 with dri2 support will fix it. It seems the compiz fusion developer won't do much regarding that topic. But there are already many discussions even here in the forum:
[http://ubuntuforums.org/showthread.php?t=769020]("http://ubuntuforums.org/showthread.php?t=769020")

---

