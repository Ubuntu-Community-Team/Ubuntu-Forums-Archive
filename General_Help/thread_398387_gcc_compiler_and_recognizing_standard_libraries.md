---
title: "gcc compiler and recognizing standard libraries"
date: 2007-03-31
forum: General Help
---

### Post by FakeFrowns on 2007-03-31
So i couldn't find a fix for this on the forums, hopefully you can help.  I'm pretty sure this should be an easy thing to fix, but i can't quite figure it out.

I'm doing some basic C programming, and i was doing it all in windows, but i wanted to try it in linux.  I copied my .c files over to my ubuntu system and tried to compile them using the gcc command. (which i have a little experience using at my university labs)

the problem i'm having is that the gcc compiler starts but throws errors saying it can't find the libraries.  like stdio.h.  so obviously it can't compile the rest of the program.  

So what do i need to do to get those properly installed?

Thanks for the help.

---

### Post by taurus on 2007-03-31
Install the build-essential package first.

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by FakeFrowns on 2007-04-01
Thanks, worked like a charm.

---

