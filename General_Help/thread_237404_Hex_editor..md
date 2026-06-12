---
title: "Hex editor."
date: 2006-08-16
forum: General Help
---

### Post by ProjectGod on 2006-08-16
Hi, 

what is a nice, popular hex editor for ubuntu linux? cheers.

---

### Post by 23meg on 2006-08-16
Check out Bless and ghex.

---

### Post by ProjectGod on 2006-08-16
i can't find bless. is it at sourceforge?

with ghex, it says the source or something is untrusted. i havent got any other repos addeded. just all of the default ones enabled. is that fine? 

cheers.

---

### Post by 23meg on 2006-08-16
Bless is here (found via Google): [http://home.gna.org/bless/](http://home.gna.org/bless/)

> with ghex, it says the source or something is untrustedI can't help you with such a vague description. Where and how exactly does this appear? When you do apt-get install?

---

### Post by ProjectGod on 2006-08-16
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  ghex libgtkhex0
Should I go ahead and install the packages anyway?

----------------------------

i get that when i 
x@y:-$ sudo aptitude install ghex

---

### Post by 23meg on 2006-08-16
This shouldn't happen if you have just the official repos in your sources.list. Maybe you somehow deleted the default keys. If you're 100% sure you don't have an untrusted third party repo in your sources.list, ignore the warning.

---

### Post by ProjectGod on 2006-08-16
please see attached. file of sources.list

---

### Post by ProjectGod on 2006-08-16
opps. sorry. looking at it again i forgot one more "#". 

but that shouldnt result in this security warning right? since that repo only contains the PPTP configuration and not actually ghex.

oh well? its working now. no more warning, since i've added another # for the last url

cheers

---

### Post by loko on 2007-06-29
Hello,

after looking a long time for a good hexeditor, i found bless. but i didn't found any deb-packages, so today i have built it by my own.

if somebody want to use it, feel free to do so.

---

### Post by mdurham on 2007-06-29
> **loko said:**
> Hello,

after looking a long time for a good hexeditor, i found bless. but i didn't found any deb-packages, so today i have built it by my own.

if somebody want to use it, feel free to do so.

Thanks for that. Mike

---

### Post by BuffaloX on 2007-07-14
> **loko said:**
> Hello,

after looking a long time for a good hexeditor, i found bless. but i didn't found any deb-packages, so today i have built it by my own.

if somebody want to use it, feel free to do so.

Thanx, I have been looking for a while now without finding anything usable.
When I tried to ./configure bless, I got some weird message about mono not being Where it's supposed to be???

So your package is very much appreciated. :popcorn:

---

### Post by mdurham on 2007-07-14
removed

---

### Post by stealth17 on 2007-08-10
> **loko said:**
> Hello,

after looking a long time for a good hexeditor, i found bless. but i didn't found any deb-packages, so today i have built it by my own.

if somebody want to use it, feel free to do so.

thanks, works great :guitar:

---

### Post by karthikbalaji on 2007-11-13
Thanks a lot buddy

---

### Post by DirtDawg on 2007-11-13
Pardon my ignorance, but why exactly does one edit hex files? After reading this thread I read about what hex files are and I'm looking at an article about disk sectors now, but I'm not grasping the basic 'why'.

---

