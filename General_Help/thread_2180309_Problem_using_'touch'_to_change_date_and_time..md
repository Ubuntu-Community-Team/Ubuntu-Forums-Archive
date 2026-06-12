---
title: "Problem using 'touch' to change date and time."
date: 2013-10-12
forum: General Help
---

### Post by Bobby_James on 2013-10-12
I want to change a filename date and time using touch.

I use:

touch -t 201301101000 filename

This should be 01 January 2013 at 10:00

However, ls -l shows:

-rw------- 1 xxx xxx    35 Jan 10  2013 filename

But, ls -l  for all other files shows:

-rw------- 1 xxx xxx  4907 Oct 12 16:09 another_filename

How can I show the time rather than the year after using touch to modify the date and time?  

Thanks!

---

### Post by steeldriver on 2013-10-12
I think that's just the default time formating for 'ls' when the file is more than 6 months old - if you want to see the full time stamp for all files regardless of age, add the --full-time switch

```
ls -l --full-time
```

or use 'stat' e.g.

```
stat -c '%y' *filename*
```

---

