---
title: "Authorizing 3v1n0-sources-list"
date: 2007-08-12
forum: General Help
---

### Post by djrobthaman on 2007-08-12
Hi,

I downloaded the 3v1n0-sources-list package from trevino's repository, and it is amazing the amount of software that I wanted was on it.  But now none of the repositories that it added are authentcated.

So, does anybody know an easy way (or a hard way) to authenticate them?

Thanks

---

### Post by hikaricore on 2007-08-12
You would need to import the signed key for each repo in that list.

If I remember correctly Trevino lists the key for them all in a comment above the actual repo info as shown here: [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

This list may vary from your own, I suggest opening your own sources.list file and adding each key to your system one by one.

---

### Post by djrobthaman on 2007-08-12
arghhh

I was hoping there'd be an easier way than that. But thanks for the link and the help.

---

### Post by hikaricore on 2007-08-12
NP, also be aware that we do not technially recommend 3rd party repos here.  If someone decides to be bad with their repo (which doesn't happen often but is possible) they can break your package system or even use it to install malicious packages (actually they don't, effectively you do lol).  Like I said these are both very unlikely, just be aware that it's possible.

Good Luck,

--Aaron

---

