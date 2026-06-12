---
title: "Beagle doesn't work"
date: 2007-01-09
forum: General Help
---

### Post by Lem on 2007-01-09
I've noticed the nautilus search and beagle find nothing - even if I enter the filename of a file clearly in my home directory. beagle-status does nothing either

I'm running a fairly fresh copy of edgy. Why isn't beagle indexing?

---

### Post by reclusivemonkey on 2007-01-10
Searching the forum is a great way to find answers to your questions;

[http://ubuntuforums.org/search.php?searchid=12539926](http://ubuntuforums.org/search.php?searchid=12539926)

---

### Post by Lem on 2007-01-10
Yes, I had tried that  :rolleyes:  (your link doesn't work btw)..

I seem to have beagle installed correctly - this is a almost virgin edgy build. I seem to have a few indexes (but hit and miss) for IM conversations but nothing else.

---

### Post by reclusivemonkey on 2007-01-10
> **Lem said:**
> Yes, I had tried that  :rolleyes:  (your link doesn't work btw)..

I seem to have beagle installed correctly - this is a almost virgin edgy build. I seem to have a few indexes (but hit and miss) for IM conversations but nothing else.

Have you given beagle time to index?

What do you get from

```

beagle-info --index-info

```

?

---

### Post by Lem on 2007-01-11
Yep, this machine has been on constantly for several days at a time.
Any command such as the one above to investigate the status of the indexing just results in the terminal window hanging waiting for the command to finish.

Something is obviously not right here. Looking at the logs, the problem might be mono - I'll try reinstalling it.

---

