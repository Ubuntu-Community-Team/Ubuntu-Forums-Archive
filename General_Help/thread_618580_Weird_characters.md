---
title: "Weird characters"
date: 2007-11-20
forum: General Help
---

### Post by muadnu on 2007-11-20
This one should be easy, but I haven't found a fix: I sometimes get very weird characters, for no specific reason that I can point out (it has to do with accents or quotes or symbols like that, but I'm not exactly sure what it is). It happens in many different programs (including Firefox, Thunderbird).

At least I know now a specific instance of the problem: I was compiling a C++ program on SciTE and got these weird characters wherever a backwards quote like ` should have been (see thumbnail). The output on a terminal is
```

IPS.h: In constructor ‘IPS::IPS(int)’:
IPS.h:18: warning: unused variable ‘STAR’
IPS.h:19: warning: unused variable ‘DRAW’

```

By the way, I'm using Gutsy 64bit. Any ideas?

---

### Post by colo on 2007-11-20
You need to make sure "plain text" files are saved and interpreted using correct the encoding. Take a look at [http://www.joelonsoftware.com/articles/Unicode.html](http://www.joelonsoftware.com/articles/Unicode.html) - it might help you understand what's going on, and how to fix it :)

---

