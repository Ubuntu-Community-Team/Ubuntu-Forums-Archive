---
title: "Update ?error? msg"
date: 2006-09-21
forum: General Help
---

### Post by JimS on 2006-09-21
...
Using Breezy on 6 year old Dell 4100, 1GHz, 512MB RAM.

When I get updates or when I want to install via 
Synaptic Package Manager, I get the following msg:

W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)

I click "OK" and seem to proceed normally.

What is this and how can I correct it?

Thanks
...

---

### Post by Iarwain ben-adar on 2006-09-21
Hi,
it is not a problem :D

Just open up your sources.list, and comment out ( => # ) the line, like this:
```
# http://koti.mbnet.fi breezy/ Packages
```

That should do the trick :D


Iarwain

---

### Post by JimS on 2006-09-21
...
Found sources.list in /etc/apt, but it is read only
so I can't comment out those lines.

How to I edit this read only file?
I would guess some sort of sudo magic.
...

I miss Belgium
...

---

### Post by mssever on 2006-09-21
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Das Goat on 2006-09-21
Thanks! that helped me too. i am such a newbie!

---

### Post by JimS on 2006-09-22
...
Good morning.
That seems to work.
Many thanks Iarwain and Mssever...
...

---

### Post by Iarwain ben-adar on 2006-09-22
Hiya,
no problem :D

btw, you said you missed Belgium?


Iarwain

---

### Post by Ramses de Norre on 2006-09-22
Who wouldn't? ;)

---

### Post by Iarwain ben-adar on 2006-09-22
:D

It's nice to see some belgian people around here..


Iarwain

---

### Post by JimS on 2006-09-22
...
I used to drive thru BE in the late 80s and early 90s
going between Germany and UK.  Once I was at a 4-day conference
in Brussels.  While there I visited 2 local Judo Clubs.
One was French and the other Flemish.  Interesting that as a foreigner
I was allowed in both clubs.  Seems to be a lot of prejudice
between the two groups.  The food was great.  Miss all of Europe.
I lived 10 years in Bayern Germany and 2 years in Jyland Denmark.

Thanks again for all the help.  This is a wonderful forum.
I always get a good answer.
...

---

### Post by Iarwain ben-adar on 2006-09-23
Hi,
it's nice to know that some people actually know where Belgium is :D

You're quite the traveler..

Btw: we love to help (on the forum ;) )


Iarwain

---

