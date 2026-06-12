---
title: "[SOLVED] Global file system search."
date: 2008-05-12
forum: General Help
---

### Post by bilijoe on 2008-05-12
I know there's a way to do this, from the command line.  I used to do it all the time, back when I was a Unix guru--but that was another life--another place in time; now I'm just a newbie again.  As I recall, the technique relied heavily on grep or egrep.  What I want to do, is to search an entire file system for a particular word (or hex string).  Does anyone know how to accomplish this,  and, if so, can you please send me the code that does it.  I'd be very appreciative. :)

---

### Post by Monicker on 2008-05-12
You want to search the entire filesystem for files containing a particular string?

```
sudo grep -r string /
```

That may take a while, depending on many files are on your system.  I would recommend narrowing it down instead of starting at /.

---

