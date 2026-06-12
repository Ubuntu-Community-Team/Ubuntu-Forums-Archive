---
title: "Serious Problem with Nautilus"
date: 2007-03-25
forum: General Help
---

### Post by xavier_r on 2007-03-25
I am posting from failsafe terminal right now...

I had installed xvidcap, byzanz to make movies of my desktop...
Then one time while running byzanz my system slowed down...
I directly clicked on shutdown without closing any apps...
Shutdown was normal...

Now when I log into my login...
Nautilus seems to consume too much memory and then it stops itself and restarts again...
This is happening cyclically...
I removed byzanz and xvidcap...(apt-get remove)
But still the system slows down drastically...

I checked other accounts and nautilus was working fine there...
I thought maybe there was some problems with configuration files...
So i deleted my ~/.nautilus directory with the hope that in the next run it will be automatically created and working fine...
But still nautilus hangs... and i am unable to use my desktop...

Can anyone help?

---

### Post by xavier_r on 2007-03-25
anyone please?
I cant use my desktop...

---

### Post by Rui Pais on 2007-03-25
> **xavier_r said:**
> ...

I checked other accounts and nautilus was working fine there...
I thought maybe there was some problems with configuration files...
So i deleted my ~/.nautilus directory with the hope that in the next run it will be automatically created and working fine...
But still nautilus hangs... and i am unable to use my desktop...

Hi,
try to delete too all ~/.gnome* folders or move it temporarily to some other place if you want to recover later your personalizations.
```
mkdir temp
mv .gnome* temp/

```
hth

---

### Post by xavier_r on 2007-03-25
Nope that didnt help...
Nautilus is still slow and crashes...

I wonder if there are any other conf files that I am missing

---

### Post by Rui Pais on 2007-03-25
> **xavier_r said:**
> Nope that didnt help...
Nautilus is still slow and crashes...

I wonder if there are any other conf files that I am missing

uhm, bad luck

try to move too .gconf and .gconfd

hth

---

### Post by xavier_r on 2007-03-25
Thanks Dude now it is working...
Although with some scratches like applets and icons are changed and stuff like that...
But its not crashing anymore...

I wonder what was the problem...
But Thanks Anyways...

---

### Post by Rui Pais on 2007-03-26
hi, no prob.

well .gconf contains the config files for gnome. 

Something (byzanz, i bet) must have done something really bad to your config files.

Of course, starting with a fresh default configuration deleted all your previous sets and personalizations :(
You may try recover some of those by moving the old .gnome* to your home folder, if you haven't done it yet, but for the most of your preferences you must set them again manually... yes, boring.

But at least you got it work again :)

---

