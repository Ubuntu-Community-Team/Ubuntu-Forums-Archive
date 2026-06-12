---
title: "Installing JRE Problems"
date: 2007-04-12
forum: General Help
---

### Post by JimmyJames88 on 2007-04-12
I have tried many times unsuccessfully to get JRE running on my machine and I'm not sure what the problem is, the reason I need it is so that my sister can use Limewire on our newly installed Ubuntu OS (I just convinced everyone in the house to get off of XP and onto Linux).  

Anyways right now my theory is that the i586 packages from Sun for the JRE may not be compatible with my Pentium 4 chip, would that have anything to do with it or am I just an idiot?  If it does have something to do with it, is there a work around?

---

### Post by aysiu on 2007-04-12
Have you tried this?
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Or considered using [Frostwire](http://www.frostwire.com/download.php?os=deb) instead of Limewire?

---

### Post by JimmyJames88 on 2007-04-12
Yes I have looked at Frostwire, but it also requires JRE.  I will have a look at the site and repost whether I figure it out or not.

Oh also, what is the real difference between Limewire and Frostwire?

---

### Post by JimmyJames88 on 2007-04-12
```
james@desktop:~$ sudo apt-get install java-gcj-compat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
java-gcj-compat is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I get this, saying it's installed but when I click on Limewire in my applications menu nothing comes up.

---

### Post by dcstar on 2007-04-12
> **JimmyJames88 said:**
> ```
james@desktop:~$ sudo apt-get install java-gcj-compat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
java-gcj-compat is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I get this, saying it's installed but when I click on Limewire in my applications menu nothing comes up.

That is not JRE, what happens when you install the sun-java5-jre package (use Synaptic)?

You should be prompted to accept the Sun licence, if you do not do this then the package will not install.

---

