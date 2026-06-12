---
title: "Unable to remove broken dependencies"
date: 2015-12-25
forum: General Help
---

### Post by tingxyu1996 on 2015-12-25
I tried to install code::blocks IDE on my Ubuntu Mate(I think it doesn't matter which DE I use) that I downloaded the debs from its official website. Then I use terminal to install those debs and the broken dependencies reported. I searched for Google for the solutions and I tried all the methods available, still the messages came out.
[IMG]http://oi68.tinypic.com/1237f5x.jpg[/IMG]

I followed sudo apt-get clean, autoremove, -f install, purge package or whatever general commands, and even I removed the code::blocks directory, that still not solve this problem. Now I can't install any debs because of unresolved dependencies, I can't open package manager too!

Any way to force remove any broken dependencies caused by code::blocks?

Additional information: the version of code::blocks downloaded from official website is 13.12-1 but from wily-werewolf repository the version is 13.12-3. Maybe version conflict?

---

### Post by ian-weisser on 2015-12-25
Yes, indeed, version conflict. Lots and lots of version conflict.
Avoid random apt incantations - they may make the problem worse.

Completely remove the incompatible upstream version, including all dependencies it may have installed.
Clean your local package cache so those incompatible packages don't get reinstalled. (sudo apt-get clean)
Disable the upstream repository. 
Since you have changed sources, refresh your package database. (sudo apt update)
Install the fully-compatible, tested version of codeblocks in the Ubuntu repositories. (sudo apt install codeblocks)

---

### Post by Bucky Ball on 2015-12-26
Just for future reference, just double click a .deb file and Software Centre (or gdebi) will install it for you. In this case, it would have told you there was a version conflict and saved you some time and hassle.

No need to install .debs from a terminal.

If you have Synaptic Package Manager, that has an option to 'fix broken packages' and gives you much more idea of what's going on. Perhaps install it and have a look.

---

