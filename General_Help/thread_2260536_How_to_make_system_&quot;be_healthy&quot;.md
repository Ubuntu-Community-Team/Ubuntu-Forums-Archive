---
title: "How to make system &quot;be healthy&quot;"
date: 2015-01-12
forum: General Help
---

### Post by fkervin on 2015-01-12
Hi all,

I've just have a problem with automatic upates (something about unmeet dependencies or something) and after this the grub has got damaged and althought system booted the grub menu appeared on every boot.

I've solve this reinstalling grub2, and now everything seems to be ok, but I would like to improve my knowledge of Linux, so I answer:

How can I make system be all healthy as possible? I mean, update all programs (something beyond sudo apt-get update && sudo apt-get upgrade?), test all dependencies, packages, erase packets not needed, test the bigger possible quantity of component...

I want to take my system and be sure that it up to date and with less "hidden problems" as possible.

Regards and thanks

---

### Post by oldos2er on 2015-01-12
```
man apt-get
``` will give a lot of info. Start with ```
sudo apt-get update && sudo apt-get dist-upgrade

sudo apt-get check

sudo apt-get autoremove

```

---

### Post by DuckHook on 2015-01-12
In addition to *oldos2er*'s good advice, by the tone of your question, it seems that you are interested in exploring and understanding your Linux system a little more than most.

If so, then I encourage you to regularly look at your system logs. This is a good way to see what your system is doing at boot, what problems it may be encountering, how it is behaving during its operation and, as a wonderful side benefit, is an excellent habit that might allow you to detect security breaches.

Ubuntu has a convenient GUI-based log viewer available through the dash called *System log*.

---

### Post by ian-weisser on 2015-01-12
> **fkervin said:**
> I mean, update all programs (something beyond sudo apt-get update && sudo apt-get upgrade?), test all dependencies, packages, erase packets not needed, test the bigger possible quantity of component...

Ah, so you want to learn about basic package management.

Good for you!

1) You need to understand the difference between dpkg and apt and the other package management tools.
See [https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html)

2) Look at the manpage for dpkg. Focus on the 'install', 'remove', 'purge', 'list', and 'search' features. Dpkg is enormously powerful

3) Try installing something big (like a media player or big application) using dpkg. This should be easy; you just read the manpage....
Then uninstall it.
Then install it again using apt-get. See the difference?

4) Look at the manpage for the 'apt-cache' command. This command lets you browse dpkg's enormously helpful database of available packages. Especially the 'search', 'show', 'depends', 'rdepends', and 'policy' features. Very, very handy.

5) Look at the manpage for apt-get. Especially the 'simulate', 'autoremove', 'reinstall', 'clean', and 'autoclean' features. This is how you identify and remove orphaned or broken packages, manage your cache of downloaded .deb files, and test actions before committing. 

6) Discover where your software comes from, and why your apt sources are the way they are:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[https://wiki.ubuntu.com/TimeBasedReleases](https://wiki.ubuntu.com/TimeBasedReleases)

---

### Post by DuckHook on 2015-01-12
Good stuff. The only minor caveat I would add is that it's never a good idea to go exploring things that form the backbone of your installation on your production box. That's how I ran into big problems some years ago: exploring *dpkg* on my base machine.:oops: Far better to do this sort of exploration in a VM and break it all you want when a simple reversion to a working snapshot will make all of the misery just go away.

---

### Post by Bashing-om on 2015-01-12
fkervin ^^ along with those thoughts

> **DuckHook said:**
> Good stuff. The only minor caveat I would add is that it's never a good idea to go exploring things that form the backbone of your installation on your production box. That's how I ran into big problems some years ago: exploring *dpkg* on my base machine.:oops: Far better to do this sort of exploration in a VM and break it all you want when a simple reversion to a working snapshot will make all of the misery just go away.

Dual boot ! .. and play in your test machine - on bare hardware - to your hearts content .. when ya break it and " all the misery " sets in, ya still have your work install to use - when it is broke, Google is your best friend. In that process of climbing out of the misery you will learn most.

[INDENT][INDENT]I did, I do, and I will 
But I sure hate when I break my 'work' install
[/INDENT][/INDENT]

---

### Post by DuckHook on 2015-01-13
:lolflag: Some people *embrace* pain. But I am old, slow, fat and lazy: a sloth who prefers the view of misery from afar over being up close and personal. Have climbed out of too much misery over the years to enjoy hitting myself on the head just for the feeling I get when it stops. But some people might be motivated by this, which I can understand ...in an intellectual sense ...kinda.

---

### Post by Bashing-om on 2015-01-13
> **DuckHook said:**
> :lolflag: Some people *embrace* pain. But I am old, slow, fat and lazy: a sloth who prefers the view of misery from afar over being up close and personal. Have climbed out of too much misery over the years to enjoy hitting myself on the head just for the feeling I get when it stops. But some people might be motivated by this, which I can understand ...in an intellectual sense ...kinda.

Lots of laughter, the voice of experience ! I had to share this with the other that makes my life better .

[INDENT]no quip here
[INDENT][INDENT][INDENT]can not top ^
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by DuckHook on 2015-01-13
Hope life keeps smiling on you, Bash ):P
...and your Sig Other!

---

### Post by fkervin on 2015-01-13
Awesome!!!

Many many thanks to all for the asnswers :).

I've start following the advices of oldos2er, and now I add this thread to favourites.

Regards and thanks again

---

