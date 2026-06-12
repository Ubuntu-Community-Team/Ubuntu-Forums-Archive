---
title: "General advice on installing bleeding-edge versions"
date: 2008-01-08
forum: General Help
---

### Post by litster on 2008-01-08
This is driving me nuts.  I love Ubuntu, but some packages, even in the latest stable releases, are literally *years* old.  In this case I want to install Imagemagick 6.3.*.  The Ubuntu version in the Gutsy repositories is 6.2.something.  It was basically created and updated in 2005.  Even Hardy Heron, when it is released, will have this old, decrepit, version of Imagemagick.  This is the one thing that drives me crazy about Ubuntu.  Everything works beautifully until you need a version of a tool that has had a certain update, or bugfix, etc. (PHP, Imagemagick, etc.) 

My question is, what is the best way to install a newer version of a tool or app that hasn't made it into the repositories yet.  I want to be able to update stuff as I need it, but still be able to remove it if the Ubuntu gods finally get around to updating old old packages.

In the case of Imagemagick 6.3.7-9, I've tried converting an rpm using alien (conflict with libmagick9 that will hose my system if I remove it), compiling from source (waiting to pull the 'make install' trigger, but scared I'll break my apt-cache or future installs of Imagemagick  if I do), considering using someone else's repositories, but scared I'll break future upgrades if I do that.

How do I do this?  If I could solve this problem, Ubuntu would be perfect.  I'm sure that other newbies have the same question for obscure tools/packages.

PLEASE HELP!

---

### Post by sub2007 on 2008-01-08
If you want bleeding edge or something not in repos, you need to compile really. Converting with alien is not (in my opinion) a great option. 

To solve your problem with make install, I always use checkinstall when compiling. You need to first install it with

```
sudo apt-get install checkinstall
```

Then the next time you compile something, instead of doing **sudo make install** you do **sudo checkinstall**. The compiling will take longer but it will then create a deb package and install it into synaptic and so if a newer version pops up in repositories then it will allow you to replace it with that. It also allows you to uninstall it with synaptic (or sudo apt-get remove).

Needless to say it's not 100% perfect, if a newer version comes into repositories it's often necessary to remove the old version and install the new one fresh rather than just updating it. And occasionally you should turn off fetching updates for the package as it may constantly nag you that there is a newer version in repositories (even though your version is newer). Still it's better than nothing.

---

### Post by LoungeLizard362 on 2008-01-08
i would suggest checking the Debian repositories, the unstable repository usually has fairly recent versions on it.  i checked for imagemagick and it's also 6.2.x, but normally it's a good place to start

[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)

---

### Post by sub2007 on 2008-01-08
> **LoungeLizard362 said:**
> i would suggest checking the Debian repositories, the unstable repository usually has fairly recent versions on it.  i checked for imagemagick and it's also 6.2.x, but normally it's a good place to start

[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
I wouldn't recommend that, it's something I've tried before and won't try again. You'll have a pain fulfilling the dependencies as Debian has different names for the packages than Ubuntu and sometimes different versions of those dependencies (especially considering it's unstable so it may use more up-to-date versions of the dependencies), so you may have to update your dependencies which may then break another package in Ubuntu that has that dependency.

That's not saying that it won't work, it's just something I wouldn't recommend.

---

### Post by bodhi.zazen on 2008-01-08
Mixing repos is not a good idea, much better to compile from source.

IF you want to mix repos, use "pinning"

ONLY install the packages you need, ie sudo apt-get update && sudo apt-get upgrade is likely to cause breakage.

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

		[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

### Post by Vinno on 2008-01-08
Isnt there a package ubuntu team or too many staff on kubuntu and all other type of ubuntu tree releases.

---

### Post by litster on 2008-04-21
> **sub2007 said:**
> If you want bleeding edge or something not in repos, you need to compile really. Converting with alien is not (in my opinion) a great option. 

To solve your problem with make install, I always use checkinstall when compiling. You need to first install it with

```
sudo apt-get install checkinstall
```

Then the next time you compile something, instead of doing **sudo make install** you do **sudo checkinstall**. The compiling will take longer but it will then create a deb package and install it into synaptic and so if a newer version pops up in repositories then it will allow you to replace it with that. It also allows you to uninstall it with synaptic (or sudo apt-get remove).

Needless to say it's not 100% perfect, if a newer version comes into repositories it's often necessary to remove the old version and install the new one fresh rather than just updating it. And occasionally you should turn off fetching updates for the package as it may constantly nag you that there is a newer version in repositories (even though your version is newer). Still it's better than nothing.
Sorry for not thanking you promptly, but thanks! Checkinstall is a great utility!  However, in my case, checkinstall wasn't able to make a package out of imagemegick. My solution was to compile imagemagick from source (scary for a first timer), and install it into another directory.  I removed the Ubuntu version of imagemagick and included the path where I compiled imagemagick in my path, like (in my .bashrc): export PATH=$PATH:/path/to/imagemagick.  Now not only does it work, but if Ubuntu ever releases an updated imagemagick package, I can erase my old one and install the new one using synaptic or apt-get.

---

