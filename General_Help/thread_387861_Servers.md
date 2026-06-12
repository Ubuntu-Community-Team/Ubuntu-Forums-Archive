---
title: "Servers"
date: 2007-03-18
forum: General Help
---

### Post by rubikfreak on 2007-03-18
When I use apt (just talking about the package manager in general) to do an update (dist-upgrade) or install a package, the servers max my connection at about 300kB/s, but after a few seconds slows down to about 30kB/s. Why is this happening?

---

### Post by scxtt on 2007-03-18
it's most likely "normalizing" ... you aren't truly getting 300kbps in those 1st few seconds ... are you sure you're using archives that are "close" to you?

---

### Post by rubikfreak on 2007-03-18
I live in the U.S. and use the default U.S. servers, so I definitely am close to them.

---

### Post by scxtt on 2007-03-18
yeah, i do too - us.archive.ubuntu.com ... but i did an nslookup on that, got the IP then did a [lookup of the IP](http://www.dnsstuff.com) - points to the UK ...

---

### Post by rubikfreak on 2007-03-18
It's really bugging me, because I've got to do a massive update at about 700 megabytes. I guess I'll just have to bear with it.

---

### Post by scxtt on 2007-03-18
you could change the us to uk and see if it makes a difference ...

---

### Post by llamakc on 2007-03-18
This seems to be a regularly-occurring issue with the us. sources. I always remove the "us." from mine, and then reload `apt-get update` and continue with my upgrade whether it is `apt-get upgrade` or `apt-get dist-upgrade`.

---

### Post by rubikfreak on 2007-03-20
I removed us. from the servers, but it still is going very slowly. What's up?

---

### Post by scxtt on 2007-03-20
try doing a traceroute from your computer to the server and see if you get anything ... i did "mtr us.archive.ubuntu.com" and saw that it goes through a lot of hops ... maybe it's more a thing w/ your ISP than their servers - which could be the case for anyone ...

for me, uk.archive.ubuntu.com takes fewer hops than us.archive.ubuntu.com - but i live in Ohio ... *shrugs*

---

