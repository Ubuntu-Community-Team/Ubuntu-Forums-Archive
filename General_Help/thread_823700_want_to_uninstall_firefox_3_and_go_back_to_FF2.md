---
title: "want to uninstall firefox 3 and go back to FF2"
date: 2008-06-09
forum: General Help
---

### Post by HappyFeet on 2008-06-09
i uninstalled FF3 and installed FF2. that didnt work. is there something else i need to do?

---

### Post by jimmy the saint on 2008-06-09
It really shouldn't be an issue.  Open synaptic, remove all ff3 packages and add ff2 packages.  are you recieving error?  what makes you think it did not work?  how did you try to uninstall/ reinstall?

---

### Post by Dougie187 on 2008-06-09
you also need to remove the firefox package as far as i know. And possibly the ubufox. Since they all want to use the firefox 3 packages. one thing you might do as well, is create a symlink called firefox in /usr/bin to /usr/bin/firefox-2 that way all your programs that load webpages will work like they should.

---

### Post by knutschr on 2008-06-09
Enable in Synaptic the proposed repositories.
Then you can install FirefoxRC2, that works fine.

---

### Post by CouchMaster on 2008-06-09
No problem - easily done via synaptic.  I would install FF2 first then uninstall FF3
I mean I've already done this on my computers this way.

---

### Post by Zorael on 2008-06-09
GUI options aside (because we all love the terminal, right?): clear the cache in FF3, exit it, and then enter the following in a terminal.
```
$ sudo aptitude purge firefox-3.0 firefox-2+
```

---

### Post by Pjotr123 on 2008-06-09
It's not wise to do this. The FF3 Mozilla engine is a very important part of Hardy, also for other functions. Better to install Epiphany alongside FF3, if you have problems with FF3.

By the way, most problems with FF3 disappear when you do this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 1 )

---

### Post by Zorael on 2008-06-09
> **Pjotr123 said:**
> It's not wise to do this. The FF3 Mozilla engine is a very important part of Hardy, also for other functions.
Now you've made me curious. Could you elaborate on this?

---

### Post by Pjotr123 on 2008-06-09
> **Zorael said:**
> Now you've made me curious. Could you elaborate on this?

I'm sorry, I have this knowledge from somebody else, whose technical knowledge of Linux far exceeds mine. I didn't check this information myself, because I trust his judgment. But of course, for other people that's not good enough. I apologize. 

I'll do my best to find the necessary information as yet: it's an important matter, so we need the source of the information for ourselves.

---

### Post by Pjotr123 on 2008-06-09
OK, first update:

Many applications use the render engine of Firefox. As Hardy is built around FF 3 and it's render engine, that particular render engine is the one that applications in the Hardy repositories are targeting (or will target in the near future, after updates). 

So it's wise to keep FF 3 on your hard disk, even if you don't use it (yet). This will ensure maximum stability of all Hardy applications. If you are unsatisfied with FF 3 in this it's prerelease quality, use alternatives like Epiphany and/or Opera, but don't uninstall FF 3.

---

