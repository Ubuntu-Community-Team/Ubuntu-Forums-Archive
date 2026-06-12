---
title: "Dyslexia &amp; File Permissions."
date: 2013-07-12
forum: General Help
---

### Post by Ashboy on 2013-07-12
Hi. I've a bit of a.. problem 'assimilating' a large chunk of text. I am dyslectic and while I can read and write, from time to time I just stumble across something I can't wrap my head around. Like this:  > [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)  I need something simple done. I have a non-system directory with a few hundred files that for whatever *all* got ROOT ownership. I have some notion why this happened, but I don't know what to do. It's messing everything up, I need to put it back to normal. I need the owner to be DISARM and the group to be Disarm, on all of them.  Can someone just.. write it out for me? I've gone over that whole FilePermissions page five times and I'm starting to get a headache. The bit at the end about needing to be super careful with some of these commands has me a little scared too.

---

### Post by cool110 on 2013-07-12
Just cd into the directory and run
```
sudo chown disarm:disarm ./*
```

---

### Post by Ashboy on 2013-07-13
Thanks, you are a life saver. :)

---

