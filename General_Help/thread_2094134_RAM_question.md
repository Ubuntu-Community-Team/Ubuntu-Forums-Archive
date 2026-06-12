---
title: "RAM question"
date: 2012-12-12
forum: General Help
---

### Post by alphaamanitin on 2012-12-12
So I have a new system76 laptop that I just installed 16 gb of ram.  I have windows 7 in virtual box that I allocated 8 gb of RAM to.  Why is it that when I run ```
free -m
``` before opening virtual box says I have 14 or 15 gb free, when I run the windows 7 in virtual box and do the command it says I have 7.8 free or so.  When I quit it still says I have 7.8 or so free.  I have noticed that it never goes down until I restart.

Is this real?  Is my locked in use or is the output of the command wrong?  

AlphaA

---

### Post by chadk5utc on 2012-12-12
that is one of several commands that will work here is the one I prefer as it gives you much more detail. Simply type:
> top
It also shows you whats using it all by process

---

### Post by pqwoerituytrueiwoq on 2012-12-12
it is probably including cached data, if you start it back up you will see no/little ram change

---

### Post by andrew.46 on 2012-12-13
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

:)

---

### Post by alphaamanitin on 2012-12-13
> **andrew.46 said:**
> [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

:)

Thanks!  I figured it was something like that as even when I only had 128 mb free I didn't see performance loss.

AlphaA

---

