---
title: "Cannot install build-essential! [Resolved]"
date: 2007-05-17
forum: General Help
---

### Post by cablejimmy on 2007-05-17
I tried
<sudo aptitude update>
then
<sudo aptitude install build-essential>
but it just brings up this:
<Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed.>

Im 99% positive the repositoris are right, so could someone please help me? I cant install anything really until I get build-essential.

I have Xubuntu 6.10, edgy-eft.

Im kind of a noob at Ubuntu, so yeah.

---

### Post by m.musashi on 2007-05-17
I have no problem. Where are you? Perhaps your repos are off line. Try installing something else and see what happens.

---

### Post by zvacet on 2007-05-18
Did you open all repositories?
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

Does your sourcelist look like this

[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

---

### Post by Pollywoggy on 2007-05-19
go here

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Then just tell the nice generator your geographic location (country), your Ubuntu flavor, and the type of computer and it will generate a list of repositories closest to you.  Put those in /etc/apt/sources.list (make a backup copy of your present file first) and then 'sudo apt-get update' and then grab the package you need.

---

### Post by aysiu on 2007-05-19
> **cablejimmy said:**
> 
Im 99% positive the repositoris are right Well, we're not.

Post the output of this command: ```
cat /etc/apt/sources.list
```

---

### Post by cablejimmy on 2007-05-20
Thanks to all of you! Especially  zvacet! your advice worked, and I got a speedy reply! I already installed zsnes immediately after.

---

### Post by aysiu on 2007-05-20
Any reason in particular that you wanted to compile *zsnes* from source instead of using *apt-get* to install it?

---

### Post by cablejimmy on 2007-05-20
Well, I changed the "flavor" of ubuntu I was using right after I posted this thread, so I don't know if I needed build-essential (to install zsnes, I used *aptitude*). I wanted to compile zsnes from the source when I had Xubuntu because I couldn't figure out how to install things using apt-get or aptitude (or the Debian). Now, with the info you guys gave me on how to edit the soucelist and open repositories (in regular Ubuntu), I was able to use that for zsnes anyway. So i guess I haven't actually needed build-essential yet, but now I can actually install things. And if I ever need to compile an application from the source, I can.

---

