---
title: "Apt-Get versus Synaptic versus Aptitude versus dpkg"
date: 2006-10-26
forum: General Help
---

### Post by Mark_in_Hollywood on 2006-10-26
I haven't been able to figure it out. So, please tell me:

is there a good reason to use apt-get over aptitude?
a good reason to use dpkg when synaptic will do?

I can't find a thing about the foregoing, yet, as a nooby with 6 months into Linux/Ub, I need to know.

---

### Post by llamakc on 2006-10-26
All of the ones you mentioned are frontends for dpkg. To read up on dpkg, type: info dpkg in a terminal.

Aptitude, Adept, Synaptic, and apt-get all use dpkg to install & manage packages.

---

### Post by az on 2006-10-26
Start here for the whole enchilada on Ubuntu package management:
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)


The nitty-gritty is that while each tool has it's advantages and weaknesses, they all handle the same packages and the same package database.  You will not run into trouble by installing something with aptitude and removing it with add-remove programs, for example.

On a side note, as a guideline for ubuntu documentation, it is suggested to say 
"use any menthod to install the following packages" with a link pointing to the installing-packages page instead of saying something like:

"sudo apt-get install apache2 libapache2-mod-php5" for the same reasons.

---

### Post by jpeddicord on 2006-10-26
Basically, use apt-get if you know the exact package you want.
Use Aptitude if you are already in the terminal and want a UI.
Use Synaptic for a complete clicky GUI.

As the previous posters have stated, all of these utilize dpkg to get the job done.

---

### Post by moore.bryan on 2006-10-26
*many in the forums urge aptitude because they claim it resolves dependencies better than apt-get.  i don't know if it's true, but i love the --with-recommends command for it...*

---

### Post by learning curve on 2006-10-26
They all work well and all have some positives and negatives.  Take the advice of experienced users when downloading and installing something.  Do it the way that they tell you to.:)

---

### Post by aysiu on 2006-10-26
> **moore.bryan said:**
> *many in the forums urge aptitude because they claim it resolves dependencies better than apt-get.  i don't know if it's true, but i love the --with-recommends command for it...*
It certainly handles dependencies *differently*. Whether it's *better* or not is up to personal preference.

Here's the difference:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by d3v1ant_0n3 on 2006-10-26
In terminal, I use aptitude rather than apt-get for the simple reason that I can type it faster and more accurately.

---

### Post by moore.bryan on 2006-10-29
> **aysiu said:**
> It certainly handles dependencies *differently*. Whether it's *better* or not is up to personal preference.

[I]very true, aysiu; i was simply stating some users actually claim it is better.  i, however, agree with you it's simply different.
[/I]

---

### Post by ejket on 2006-10-29
I find apt-get faster than the gui, even when I have to do an apt-cache search for the exact package name ... aptitude I find weird and dangerous, for example, it always wants to remove all the kubuntu files I've installed, so if I want to use it without trashing those, I have to include kubuntu-desktop in my install string.  Bizarre.

I like synaptic for browsing around in the packages.  I've found some nice progs I've never heard of that way.

For those who think the result in terms of the installed package is different when you use different front-ends, well, I think not, but you should pay attention to what actions will be taken (you're always informed of this).

---

### Post by ~LoKe on 2006-10-29
To me, aptitude seems quite a bit slower than apt-get.

---

### Post by Azakus on 2006-10-29
I use the managers this way: Synaptic if I need to pick one of many types of software, like a media player; aptitude for packages that synaptic doesn't like and for more options in resolving dependencies; and apt-get for exact packages.
I've had instances where aptitude will download packages that synaptic doesn't list. Particularly mplayer, which wasn't listed in amd64, but aptitude found and installed.

---

