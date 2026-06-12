---
title: "package management"
date: 2014-05-30
forum: General Help
---

### Post by chadmichael on 2014-05-30
What's the difference, functionally, between using the Software Center and using Synaptic.  I'm very familiar with Synaptic, so, if there's not a killer feature, I could do without the amazon adds :)

---

### Post by TheFu on 2014-05-30
All the package mangers are based on the back-end libraries for APT.  apt-get, dpkg, aptitude, synaptic, and software-center all work on APT and the libraries, DBs used to maintain the system.

I've never used software center - not once.

You can google to remove all the external search (lense) packages from the system - it will speed up everything.

BTW, I find that aptitude is smarter about dependency resolution than the other options, plus it works when there isn't any GUI installed.

---

### Post by LastDino on 2014-05-30
As it is now, Software centre is not anywhere close to Synaptic in terms of functionality or usability. I do use it, but to only install Synaptic. And I used to use it frequently till I got to know about Synaptic as I'm actually an Windows migrant and have a general Windows *GUI way* mentality.

---

### Post by chadmichael on 2014-05-30
Thanks!  That's what I thought.

---

### Post by deadflowr on 2014-05-30
Software Center is okay for installing/removing packages.
It is not a package manager like synaptic, which has robust abilities like updating existing packages, or fixing broken packages.

That said, software center, for what it does, is easier to understand and use.
It's built for simplicity.

To add, though, I don't know what is meant by Amazon ads.
None of the banners that scroll across the top are Amazon related(from what I can tell), but instead are promotions for packages that exist within the ubuntu repo ecosystem.
Nothing wrong with promoting the more popular packages, is there?

---

