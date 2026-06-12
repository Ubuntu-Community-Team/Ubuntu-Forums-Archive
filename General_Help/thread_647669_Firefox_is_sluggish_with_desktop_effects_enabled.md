---
title: "Firefox is sluggish with desktop effects enabled"
date: 2007-12-22
forum: General Help
---

### Post by robitor on 2007-12-22
Hi, i am using ubuntu feisty with an ati X1300 card using the ati proprietary drivers. 

When I enable desktop effects, firefox scrolls very slow. And everything within firefox is basically extremely sluggish. Whenever i type something, it takes it at least 5 seconds to actually show up on the screen. When desktop effects are disabled firefox works fine.

Can somebody please help me resolve this issue?

---

### Post by ed-koala on 2007-12-22
Will need a bit more info to narrow down the problem.
Are you using Compiz for desktop effects?  If so, what effects are enabled?
How much RAM and video memory do you have?
Have you checked System monitor to see what programs are using CPU resources?
Each of these could cause your system to run slugishly.

---

### Post by stunner on 2007-12-22
My firefox has gotten slower as well (though not quite as slow, typing is still responsive).  It's not always slow, but basically whenever a new page is loading, whether in the current tab or another one, CPU hits 100%.  Scrolling quickly is also CPU intensive.  I have compiz enabled, but it is otherwise smooth.  1 gb ram, video card has 128mb iirc.

---

### Post by alanholpin on 2007-12-28
There is a simple way to solve this problem- use Opera!  At least for me there is no loss of performance with opera whilst using compiz, whereas I have the same problems as you do with Firefox.

---

### Post by stunner on 2007-12-28
Thanks for the suggestion.  I read up on some FF extension equivalents (see [http://virtuelvis.com/archives/2005/01/opera-and-firefox-extensions](http://virtuelvis.com/archives/2005/01/opera-and-firefox-extensions) and the link at the bottom) and probably 90% of the functionality I have in FF is in there, which is encouraging and bodes well for opera's future.  I'm still wary of using a closed-source app for web browsing however - it just adds another layer of worry in terms of security.  The lack of apt-getness is also a drawback.

---

### Post by lvleph on 2007-12-28
You could check swiftfox. I have not used it yet, but will when I get home. It is supposed to be optimized for your cpu or something.

---

### Post by Craigus on 2007-12-28
> The lack of apt-getness is also a drawback.

Well, it isn't hard to install. The Opera download site has .deb packages for all ubuntu versions. You just download the appropriate .deb and you can then install it in the gui by clicking on it.

---

### Post by lightstream on 2007-12-29
Opera is actually in the repositories and you can install by Add/Remove in the menu at least - you just have to make sure Add/Remove is set to show 'All Available Applications'

---

### Post by stunner on 2007-12-29
> **Craigus said:**
> Well, it isn't hard to install. The Opera download site has .deb packages for all ubuntu versions. You just download the appropriate .deb and you can then install it in the gui by clicking on it.

I was actually referring to getting updates in apt.  Sorry for the ambiguity.

> **lightstream said:**
> Opera is actually in the repositories and you can install by Add/Remove in the menu at least - you just have to make sure Add/Remove is set to show 'All Available Applications'


$ sudo apt-get install opera
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

```

According to [this post]("http://ubuntuforums.org/showpost.php?p=3194087&postcount=7") there appears to be a feisty commercial repo and an official opera repo.  And indeed, [http://deb.opera.com/opera/pool/non-free/o/opera/](http://deb.opera.com/opera/pool/non-free/o/opera/) has 9.2 from Dec. 19th.  Sweet!  I may give this a whirl to see what it's all about.

---

### Post by stunner on 2007-12-29
> **lvleph said:**
> You could check swiftfox. I have not used it yet, but will when I get home. It is supposed to be optimized for your cpu or something.

Let us know how it goes.  I don't know if cpu-optimization does anything specific to speedup operation under compiz, but I'm interested in knowing how it works out.

---

