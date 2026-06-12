---
title: "Anyone manage to get Flock working in Linux?"
date: 2008-05-08
forum: General Help
---

### Post by WinterWeaver on 2008-05-08
Hi all,

Downloaded Flock for linux last night.

[www.flock.com](www.flock.com)

After unziping etc. I tried to run it. It looks as though it's trying to load (waiting curser) but it never starts up.

Anyone else manage to get it working?

ta,

WW

---

### Post by kesman on 2008-05-08
Have you tried running it from terminal to see any error messages?

---

### Post by WinterWeaver on 2008-05-08
AHA !! didn't think of that...

The mystery revealed itself ... I am missing a package.. will install now.

---

### Post by WinterWeaver on 2008-05-08
Whoops... talked too fast.
I'm not technically missing a package, it is installed. This is the error:

```
/flock-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

EDIT: I have version 6 libstdc++ installed, and it seems as though it is looking for version 5.... can I have both installed on my system, or will it cause conflicts?

---

### Post by WinterWeaver on 2008-05-08
OK.. it's working now. I installed ver5 libstdc++ and now I have both ver 5 and 6.. no problems thus far. and flock is working fine :)

---

