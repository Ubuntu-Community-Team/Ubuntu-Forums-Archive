---
title: "Gccg, 32 and 64 bit"
date: 2015-03-15
forum: General Help
---

### Post by sladigar2 on 2015-03-15
Hello all.

I've been running Ubuntu 14.04 for awhile now, and decided tonight to play some MTG. Looked around and found that gccg would be the optimal way to do this on my laptop. Followed all the instructions on the site, got everything I figured I would need, and ran the ./Mtg command. I was rewarded with this:

```
user@laptop:~/gccg$ ./Mtg
Running ./ccg_client mtg.xml
./ccg_client: error while loading shared libraries: libSDL_net-1.2.so.0: cannot open shared object file: No such file or directory
user@laptop:~/gccg$ 
```

Though a tad odd, I popped that into Google, found that the code was compiled for 32 bit, and I'm running 64 bit. And that's as far as I've gotten. I've installed additional libraries, recompiled after updates, lots of things, and I keep getting that error. Am I missing something really simple? Or am I just doomed to not running gccg on my *nix computer?

---

