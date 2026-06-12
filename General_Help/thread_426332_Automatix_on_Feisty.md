---
title: "Automatix on Feisty?"
date: 2007-04-28
forum: General Help
---

### Post by mskadu on 2007-04-28
Whats up with Automatix2 on Fiesty? Is it no longer supported?

---

### Post by taurus on 2007-04-28
You don't need Automatix2.  Whatever you need, you can install it with synaptic/apt-get/aptitude.  What do you have in mind, anyway?

---

### Post by canadianwriterman on 2007-04-28
Yes, Automatix2 is available for Feisty:

[http://http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29]("http://http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29")

Automatix is not supported by this Forum, however (Automatix has its own Forum). It is usually recommended that you use with caution, as changes to things like your repositories, can impact future Ubuntu updates.

---

### Post by mskadu on 2007-04-28
Oh, nothing specific. I had been using with Edgy. However, when i (auto)upgraded to Fiesty it stopped working. 

I have now removed it.

> **taurus said:**
> You don't need Automatix2.  Whatever you need, you can install it with synaptic/apt-get/aptitude.  What do you have in mind, anyway?

---

### Post by taurus on 2007-04-28
And don't forget to remove those repos in /etc/apt/sources.list that automatix has created.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by mskadu on 2007-04-28
Sure. Thanks for the tip.

> **taurus said:**
> And don't forget to remove those repos in /etc/apt/sources.list that automatix has created.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by kelvin spratt on 2007-04-28
automatix is fine i use it don't take notice of them i also use the get deb web site for things ican't readilly geg as well

---

### Post by mskadu on 2007-04-28
:) Thanks Kevin. I know. However, I am set for now since Automatix has given me most of what I need. Removing it (for now) is a part of my personal "thing" that I remove whatever i dont need and re-install it whenever I do.

Thanks again :KS


> **kelvin spratt said:**
> automatix is fine i use it don't take notice of them i also use the get deb web site for things ican't readilly geg as well

---

