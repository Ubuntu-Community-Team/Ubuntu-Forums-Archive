---
title: "w32codecs in Ubuntu7.10"
date: 2007-11-21
forum: General Help
---

### Post by alphabeatsco on 2007-11-21
guys, im new to linux...I've installed Ubuntu 7.10 which has Gcc4.0 & Libstdc ++6 installed automatically...
w32codec requires libstdc++5 & gcc-3.6base
so how do i install?
i tried evverything that was on the web..
like
sudo apt-get install w32codec, it complains dependencies is missing..what can i do!?

---

### Post by fragos on 2007-11-21
Just go to [http://www.medibuntu.org/](http://www.medibuntu.org/) and add there repository.  They have what you need and other fun things in deb packages for Ubuntu.

---

### Post by prince_niceguy on 2007-11-21
or use automatix to install the same for you..

you can get it from getautomatix.com

---

### Post by mikewhatever on 2007-11-21
The instructions on installing them are fairly simple either by adding the repoisitory or by downloading the individual debs first and then sudo dpkg -i .... 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by ThrobbingBrain66 on 2007-11-21
w32codecs isn't in the Ubuntu repos, so unless you've added a 3rd-party repo like [Medibuntu]("http://www.medibuntu.org/"), you won't be able to install it.

Also, w32codecs (installed using Medibuntu) doesn't have any dependency on any gcc package.  It IS dependent on libstdc++5, but the dependency is >=, so you shouldn't have any issues (libstdc++5 and ++6 can be installed at the same time).

For what it's worth, w32codecs are working fine for me.

---

### Post by hikaricore on 2007-11-21
> **prince_niceguy said:**
> or use automatix to install the same for you..

you can get it from getautomatix.com

**[SIZE="4"][COLOR="Red"]NO NO.  DO NOT USE AUTOMATIX FOR THIS[/COLOR][/SIZE]**

---

### Post by prince_niceguy on 2007-11-21
I use automatix. I am not sure why you are recommending against it. can you let me know so that I too will also stop doing if it is dangerous..

---

### Post by dasunst3r on 2007-11-21
I used to swear by Automatix, but everything has gotten so easy, you really don't need it.  +1 for adding the Medibuntu repository.

---

