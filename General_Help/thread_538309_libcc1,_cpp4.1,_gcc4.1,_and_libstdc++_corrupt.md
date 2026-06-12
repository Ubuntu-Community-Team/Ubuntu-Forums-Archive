---
title: "libcc1, cpp4.1, gcc4.1, and libstdc++ corrupt"
date: 2007-08-29
forum: General Help
---

### Post by Adiuvo on 2007-08-29
So, I wanted to get back into C++ coding, and I used Anjuta as my IDE.

Just to test things out, I make a basic Hello world program, try to compile it, Anjuta spits out an error that gcc isn't installed, so I go to the Debian website and install it, or at least try to. Anyway, it needed some other libs that I didn't have, so I started installing those. Everything was going fine and dandy, until one lib spews out that these were corrupt. Fun. 

I tried using the terminal and typing sudo apt-get install -f like the installer told be too, but it said to remove a lot of lot of needed things, which naturally I didn't agree too. [Here's the error.]("http://www.megaupload.com/?d=IS2EFJ85") It's rather large, so I just decided to make it a TXT file. If you want it uploaded somewhere else, just tell me.

So, what I want to know is how I can correct these issues, or if it's OK to uninstall then reinstall all those libs it wanted to get rid of.

And sorry for all these threads I've been making, I'm a Linux noob :(

Thanks!

---

### Post by bmorency on 2007-08-29
you said you installed gcc from the debian website, did you only install one package? 

try this in the console:

sudo aptitude install build-essential

that will install all the packages you need to compile programs.

---

### Post by Adiuvo on 2007-08-29
Dang, that fixed everything, thanks :D

Any good guides to the terminal you have on hand? I never knew so many things were built in like that, it's great!

---

### Post by bmorency on 2007-08-29
> **Adiuvo said:**
> Dang, that fixed everything, thanks :D

Any good guides to the terminal you have on hand? I never knew so many things were built in like that, it's great!


here is a site with some guides that you might find useful. [ The Linux documentation project website.]("http://tldp.org/guides.html")

you can also go to the official ubuntu package website [here ]("http://packages.ubuntu.com/") to find package names. they are sorted by different categories too.

---

