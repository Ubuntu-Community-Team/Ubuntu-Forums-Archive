---
title: "Java for Xubuntu"
date: 2006-11-30
forum: General Help
---

### Post by I_Love_Cheese on 2006-11-30
Good Morning!

I am a brand new Xubuntu user, having just yesterday installed it on an older machine I had sitting around. 

I need Java for some basic game playing on this system.  I found Sun Java for Linux ... is this what I need?  In FireFox, I am able to download the necessary addon to the desktop, but how do I install from there?

I know this is probably a sub-basic question, but like I said, I'm new.  


Thanks for any help.

---

### Post by taurus on 2006-11-30
Use automatix2 to install it, [http://www.getautomatix.com](http://www.getautomatix.com).

---

### Post by I_Love_Cheese on 2006-11-30
> **taurus said:**
> Use automatix2 to install it, [http://www.getautomatix.com](http://www.getautomatix.com).

Right on, thanks!

---

### Post by doobit on 2006-11-30
That's too easy. :) 
Try doing it using the instructions for a manual install on the Java site. It's not too hard to follow steb-by-step, and might be worth the experience for you.

---

### Post by I_Love_Cheese on 2006-11-30
> **taurus said:**
> Use automatix2 to install it, [http://www.getautomatix.com](http://www.getautomatix.com).

Their site appears to be down.  Any other mirrors you happen to know of?

Thanks...

---

### Post by taurus on 2006-11-30
Yes, the site is currently down.  You can wait for it to come back up or you can install it by hand or you can also use easyubuntu...

---

### Post by Ramses de Norre on 2006-11-30
```
sudo aptitude install sun-java5-bin
sudo update-java-alternatives -s java-1.5.0-sun
```
Make sure you've got uni- and multiverse enabled.

---

### Post by I_Love_Cheese on 2006-11-30
> **Ramses de Norre said:**
> ```
sudo aptitude install sun-java5-bin
sudo update-java-alternatives -s java-1.5.0-sun
```
Make sure you've got uni- and multiverse enabled.

How do I enable those?  Help a noob!!!

Thanks!

---

### Post by taurus on 2006-11-30
You need to edit your /etc/apt/sources.list and remove the # sign in front of the lines with universe & multiverse...

```
gksudo gedit /etc/apt/sources.list
```
Save it and run

```
sudo aptitude update
sudo aptitude install sun-java5-bin
sudo update-java-alternatives -s java-1.5.0-sun
```

---

### Post by I_Love_Cheese on 2006-11-30
[QUOTE=taurus;1828512]You need to edit your /etc/apt/sources.list and remove the # sign in front of the lines with universe & multiverse...

```
gksudo gedit /etc/apt/sources.list
```
Save it and run

```
sudo aptitude update
sudo aptitude install sun-java5-bin
sudo update-java-alternatives -s java-1.5.0-sun
```[/

When I use gksudo gedit /etc/apt/sources.list, I get a box asking for my password.  After I enter password, nothing happens...

---

### Post by Perfect Storm on 2006-11-30
If you want the latest and have the .deb package: [http://ubuntuforums.org/showpost.php?p=1657882&postcount=7](http://ubuntuforums.org/showpost.php?p=1657882&postcount=7)

---

### Post by I_Love_Cheese on 2006-11-30
I also installed easyubuntu, but nothing happens when I choose it from "applications" ...

arg!

---

