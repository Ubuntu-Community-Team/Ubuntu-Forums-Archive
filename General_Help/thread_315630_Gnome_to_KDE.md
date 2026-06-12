---
title: "Gnome to KDE"
date: 2006-12-09
forum: General Help
---

### Post by dontgetshocked on 2006-12-09
Anyway to switch to kde instead of gnome?

---

### Post by taurus on 2006-12-09
```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
Log out and in the Sessions, bottom left corner, pick KDE and log in...

---

### Post by Malakia on 2006-12-09
Or if you don't want everything that comes with Kubuntu you can do 
```

sudo aptitude install kde-core

```
which is a lighter version of Kde
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

---

### Post by PriceChild on 2006-12-09
You can then purge gnome via: [http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

---

### Post by quarkhirad on 2006-12-09
> **dontgetshocked said:**
> Anyway to switch to kde instead of gnome?


Open synaptics and then click on the sections tab at the bottom left corner and then in the left menu scroll down till u get the title KDE Desktop Environment. There are three parts just click on them and the see the pakages  in there and install whatever u want

---

### Post by aysiu on 2006-12-09
> **quarkhirad said:**
> Open synaptics and then click on the sections tab at the bottom left corner and then in the left menu scroll down till u get the title KDE Desktop Environment. There are three parts just click on them and the see the pakages  in there and install whatever u want
I don't know what you mean about "three parts." To install KDE, you need to pick only one part and install that one part. There are several parts you can choose from, and I **definitely** would not install it using Synaptic--doesn't leave you an easy way to uninstall it later.

This is the best way to install KDE:
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

If you don't like *kubuntu-desktop*, you can install one of these instead:

*kdebase* - absolute barebones KDE--barely functional
*kde-core* - just enough to be functional and a lot faster than Kubuntu
*kde* - all the KDE bells and whistles

---

### Post by dontgetshocked on 2006-12-09
Thanks ALL


KDE is truly for me after trying many distros and (Gnome & Kde).Wish I had installed Kubuntu from the beginning although I don't know the difference between what I have now and what it would be if any. I know preferences are as noses, but this is for me.


Thanks Again


Dave

---

### Post by aysiu on 2006-12-09
> **dontgetshocked said:**
> Thanks ALL


KDE is truly for me after trying many distros and (Gnome & Kde).Wish I had installed Kubuntu from the beginning although I don't know the difference between what I have now and what it would be if any. I know preferences are as noses, but this is for me.


Thanks Again


Dave
You can get rid of Gnome using this:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by max.diems on 2006-12-09
I also have to recommend that people who say they've compared KDE to GNOME look at XFCE. Replace kubuntu-desktop with xubuntu-desktop in tutorials that explain installation.

---

### Post by quarkhirad on 2006-12-11
> **aysiu said:**
> I don't know what you mean about "three parts." To install KDE, you need to pick only one part and install that one part. There are several parts you can choose from, and I **definitely** would not install it using Synaptic--doesn't leave you an easy way to uninstall it later.


i am sorry aysiu by three parts i ment the three sections in synaptics called  KDE Desktop environment,KDE Desktop environment (multiverse) and KDE Desktop environment (universe)

Ok aysiu u claim that synaptics is not good but when i use apt-get isn't it the same as using synaptics???

---

### Post by aysiu on 2006-12-11
> **quarkhirad said:**
> i am sorry aysiu by three parts i ment the three sections in synaptics called  KDE Desktop environment,KDE Desktop environment (multiverse) and KDE Desktop environment (universe) And what I'm saying is that you don't need to select three different sections at all. There's only one package you install--*kubuntu-desktop*

> 
Ok aysiu u claim that synaptics is not good but when i use apt-get isn't it the same as using synaptics??? Yes. That's why you use *aptitude* instead of *apt-get*.
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by dontgetshocked on 2006-12-15
I need to go back to gnome, dont like this version of kde, it is not a full blown version, side effects. 


I used the terminal to change with

---

### Post by aysiu on 2006-12-15
If you used *aptitude*, you can just do ```
sudo aptitude remove kubuntu-desktop
``` And if you like the full-blown version of KDE, just do this: ```
sudo aptitude update
sudo aptitude install kde
```

---

### Post by dontgetshocked on 2006-12-15
Ok, I un-installed as per sudo aptitude remove-kunbuntu-desktop
Now, what do I need to do if anything to make suert my desktop is back as it was before I elected to replace gnome with kde ?

I want gnome, not kde !

---

### Post by aysiu on 2006-12-15
> **dontgetshocked said:**
> Ok, I un-installed as per sudo aptitude remove-kunbuntu-desktop
Now, what do I need to do if anything to make suert my desktop is back as it was before I elected to replace gnome with kde ?

I want gnome, not kde !
**If** you installed it originally using these commands ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` then the command I gave you should restore you back to normal. KDE should no longer be installed.

Did you install it using those commands? What commands did you use to install KDE?

---

### Post by dontgetshocked on 2006-12-15
Yes, above commands are correct

---

### Post by aysiu on 2006-12-15
> **dontgetshocked said:**
> Yes, above commands are correct
Then KDE should be gone now.

If not, then you can try this:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Jimi... on 2006-12-15
> **taurus said:**
> ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```
Log out and in the Sessions, bottom left corner, pick KDE and log in...

> **Malakia said:**
> Or if you don't want everything that comes with Kubuntu you can do 
```

sudo aptitude install kde-core

```
which is a lighter version of Kde
[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

Spot on, used these suggestions and KDE is boss, prefer KDE to Gnome, more accesible.

---

