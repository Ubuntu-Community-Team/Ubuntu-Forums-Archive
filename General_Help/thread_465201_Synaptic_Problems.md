---
title: "Synaptic Problems"
date: 2007-06-05
forum: General Help
---

### Post by merlinus on 2007-06-05
I installed Ubuntu on an old Compaq Evo N600C using the Alternative Desktop CD.  Everything seems to be working very well indeed, except that when trying to install any new apps via Synaptic, I am prompted for the installation cd.

This is not recognized, however, although I know the drive is working properly.  I also tried loading the regular live installation cd.

I then get an error message about missing libraries.

So it would seem that not everything needed for Synaptic was loaded with the alternate installation.

Help appreciated!

Many thanks....

-merlin

---

### Post by zvacet on 2007-06-05
sysrem>administration>software properties>unchek CD repo or 

```
gksudo gedit /etc/apt/sources.list
```

and comment (put # sign in front of the line) Cd realese line

---

### Post by merlinus on 2007-06-05
Brilliant!!!

Thanks.

BTW, the CD option never even had checkboxes on my other two Ubuntu machines.

-merlin

---

### Post by wpshooter on 2007-06-05
> **merlinus said:**
> Brilliant!!!

Thanks.

BTW, the CD option never even had checkboxes on my other two Ubuntu machines.

-merlin

Merlinus:

I am with you, this baffles me as to why this check box for the CD is apparently marked by default on some versions of Ubuntu and not on others and as far as I can tell MAY not be needed on any of them.  

Is this possible for someone that would not have any internet connection ?  If it is, then this seems like very poor thinking to me, because I can not phathom why anyone would want to attempt to run an O/S like this without and internet connection !!!  I am just wondering if this is some sloppy programming.

P. S. - I have seen on some installations that I did where there would be 2 entries for this CD, 1 checked and 1 not checked.  And I know for sure that I don't have but 1 CD drive on any of my machines.

---

### Post by merlinus on 2007-06-05
> 
P. S. - I have seen on some installations that I did where there would be 2 entries for this CD, 1 checked and 1 not checked. And I know for sure that I don't have but 1 CD drive on any of my machines.


Yes, this was the case on the laptop!  One CD drive, two entries, one checked.

Go figure....

Maybe they want to keep us from getting complacent!  LIke changing hd's to sd's, and then back again....

:)

-merlin

---

### Post by zvacet on 2007-06-05
That option is cheked by default,because you can install some packages from CD(build-essential for example).

---

### Post by wpshooter on 2007-06-05
> **zvacet said:**
> That option is cheked by default,because you can install some packages from CD(build-essential for example).

That's sort of what I thought but is that sort of a poor design, in that, isn't the latest and greatest version of everything more than likely to be found by pulling from a server than from the original installation CD ?  Is there anything on the CD that can not be pulled from somewhere else assuming you have internet connection ?

Thanks.

---

