---
title: "Simple plotting utility"
date: 2008-02-16
forum: General Help
---

### Post by jfl on 2008-02-16
Hi Good People,
I have written a program in Perl that calculates 2 sets of value - each set being stored in an array (could be put in a hash if necessary). 
 I am looking for a **simple** way  to create a *rough* cartesian plot using the first value of the set as "x" and the second as "y" coordinates. It does not need to be pretty or to be printed.
GNUplot seems to be an overkill, a Perl module would be ideal
After a 2 hours search  I am totally confused ...
Running Perl 5.8.8 under Ubuntu 7.10.
Thanks for your help.
Just another Perl Beginner !

---

### Post by s3gfault on 2008-02-16
how about just printing out the map one line at a time to the console?  That would take way less than 2 hours.

---

### Post by bilge.tutak on 2008-02-16
Actually Gnuplot is still pretty simple, but you can try XYplot. The other alternative is search ubuntu reps for "plot" keyword. You will get a lot of different plotting programs. Most of them are pretty simple.
You can use GUI for search or
```
apt-cache search plot 
```
will search the packages with keyword "plot"

---

### Post by jfl on 2008-02-17
duplicate

---

### Post by jfl on 2008-02-17
> **s3gfault said:**
> how about just printing out the map one line at a time to the console?  That would take way less than 2 hours.
[FONT="Comic Sans MS"][SIZE="3"]Yeah ! about 4 minutes !!! Just what I wanted.
Why didn't I think of it ???
Reminds of the days of DOS v1.3 on a TRS-80  :)
Thanks !!![/SIZE][/FONT]

---

