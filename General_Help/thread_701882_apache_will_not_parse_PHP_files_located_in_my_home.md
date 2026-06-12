---
title: "apache will not parse PHP files located in my home directory, will if in /var/www"
date: 2008-02-19
forum: General Help
---

### Post by wilshire on 2008-02-19
It works fine if the file is in /var/www. 

I tried copying the PHP script to /var (and /etc, just for the hell of it) and setting up apache to use one and then the other of those as the root directory. works in those places as well.

it works fine everywhere but my home directory, so i think it's a permissions thing. but i have the permissions set so that every user can read that directory.... and apache seems to have no problem reading from there, because it can serve html pages from there just fine.... it just cannot parse php from there.

i even chmod 777'd the php file in question. still no go. 

i'm very new at apache. what am i missing here?

---

### Post by wilshire on 2008-02-19
upon further testing, the ONLY directory it will not work in is the one i want it to, which is the very bottom of a generic created hierarchy in /home

:confused:

---

