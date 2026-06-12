---
title: "difference between xubuntu and ubuntu plus xfce"
date: 2007-10-24
forum: General Help
---

### Post by markp1989 on 2007-10-24
i was wondering if there is any difference between xubuntu and ubuntu except the desktop environment?

---

### Post by mojoman on 2007-10-24
Yes, there is. They come with different applications. The base system as such are the same regardless if you use ubuntu, xubuntu or kubuntu, they only differ in the desktop environment and default applications. This in turn mean that they differ in what libraries they use. 

Gnome and Xfce4 both uses gtk libraries whereas KDE favor qt libraries so xubuntu and ubuntu have a lot of libraries and packages in common, however, Xfce don't use a lot of the heavier and bloated Gnome dependencies. But the answer to your question is, yes, they also come with different applications. 

/mojoman

---

### Post by markp1989 on 2007-10-24
thanks for a quick  reply, i would also like to know how networking is done in xubuntu, i am thinking of testing it out on my laptop, so easy wireless use is a must have, i know that gnome has the nm-applet, is there a similar thing for xfce?

---

### Post by rich.bradshaw on 2007-10-24
Xubuntu uses the same nm-applet - you can run gnome (gtk) apps in xfce no problem.

---

### Post by markp1989 on 2007-10-24
cool, im gona give xubuntu a try on my laptop some time tonite or tomorrow 

thankyou for you help

---

### Post by mojoman on 2007-10-24
If you're using xubuntu in order to keep a lean and light system I'd recommend that you keep a close eye one what dependencies are installed when straying into Gnome stuff (and I'd stay clear of any KDE stuff altogether).

I couldn't find any package called nm-applets but if you're referring to gnome-applets that package, for example, will install 29 additional packages as dependencies. If you look around, you'll find light-weight applications for just about anything.

/mojoman

---

### Post by markp1989 on 2007-10-24
does any one know of any light weight network managers?

---

### Post by mojoman on 2007-10-25
Sure, I know loads. Have a look at these threads, and if you need something more, just post what it is you need to do lightweight and I'll see if I can come up with something.

[_http://ubuntuforums.org/showthread.php?t=588647_]("http://ubuntuforums.org/showthread.php?t=588647")

[_http://ubuntuforums.org/showthread.php?t=587367_]("http://ubuntuforums.org/showthread.php?t=587367")

[_http://ubuntuforums.org/showthread.php?t=382137_]("http://ubuntuforums.org/showthread.php?t=382137")

[_http://ubuntuforums.org/showthread.php?t=33183_]("http://ubuntuforums.org/showthread.php?t=33183")

/mojoman

---

### Post by markp1989 on 2007-10-25
thanks for all the links i am looking through them now

---

### Post by mojoman on 2007-10-26
I don't use a network manager myself but I think that the one that comes by default with gnome is not dependent on the heavier gnome libraries. To install it, just open a terminal and type:
```

sudo apt-get install network-manager
```

How you install stuff comes down to personal preferences but I like CLI. If you want to keep a lightweight system, get in the habit of simulating all installs first, just to see what dependencies it pulls. To simulate an install, just add the option -s, like so;

```
sudo apt-get install -s network-manager
```

That way, you'll always see what's getting installed *before* it gets installed. If it pulls down half of Gnome or KDE, then it might be a good idea to not install and find an alternative instead. There are *always* lightweight alternatives to ordinary applications.

/mojoman

---

