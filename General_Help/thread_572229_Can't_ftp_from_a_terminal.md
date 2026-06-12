---
title: "Can't ftp from a terminal"
date: 2007-10-10
forum: General Help
---

### Post by Carl H on 2007-10-10
At the command line, when I try to ftp to a remote server, it just times out after I enter my username.

But when  I use gFTP (with the same username, password, etc), it works just fine. 

What's going on?

---

### Post by thirddeep on 2007-10-10
Sounds like passive problems.

Try the following:
```

ftp
passive
open SITE
```

See if that works.

Thd.

---

### Post by Carl H on 2007-10-10
Nope, that didn't make any difference. 

Also tried it as sudo, just in case.... but no difference.

---

