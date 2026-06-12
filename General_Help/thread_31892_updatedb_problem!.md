---
title: "updatedb problem!"
date: 2005-05-05
forum: General Help
---

### Post by elpamperolo on 2005-05-05
Hi everyone. I try to run updatedb, but I get this error:

```
root@darkmoon:/ # updatedb
fatal error: updatedb: create_db(): rename: No such file or directory
``` 

I googled for this and all answers suggested a PATH problem, but, to me, it seems ok:

```
root@darkmoon:/ # echo $PATH 
/sbin:/bin:/usr/sbin:/usr/bin:/usr/bin/X11:/usr/local/sbin:/usr/local/bin
``` 

Any hint?

---

