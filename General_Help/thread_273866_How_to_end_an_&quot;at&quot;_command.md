---
title: "How to end an &quot;at&quot; command?"
date: 2006-10-08
forum: General Help
---

### Post by BitTorrentBuddha on 2006-10-08
Hi, I was looking around for how to end the things which are to be executed *at* said time. A quick google yielded <EOT>, however that didn't work, nor did reading the man page. Anyone experience with this, I would greatly appreciate the help, the at command seems to be a very useful command.```
samm@ubuntu:/tmp$ at 10:04pm
warning: commands will be executed using /bin/sh
at> echo "test"
at> <EOF>
at> <EOT>
at> EOT
at> <eot
at> <eot>   
at> <eoa>
at> end
at> exit
at> stop
at> end
at> ...
```

---

### Post by GStubbs43 on 2006-10-08
ctrl+c?

---

### Post by 3rdalbum on 2006-10-09
Ctrl+d ends the at command.

---

