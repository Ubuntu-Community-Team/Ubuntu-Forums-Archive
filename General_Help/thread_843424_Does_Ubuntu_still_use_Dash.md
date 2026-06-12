---
title: "Does Ubuntu still use Dash?"
date: 2008-06-28
forum: General Help
---

### Post by Ballena on 2008-06-28
Hello

I just wonder if Ubuntu still uses the lightweight version of Bash called Dash. I found this document and started to wonder if it still is like that: [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

Thanks
/Ballena

---

### Post by vishzilla on 2008-06-28
Yes! you can look up /etc/shells for the shells you can use

---

### Post by sdennie on 2008-06-28
Actually, it doesn't use dash for bash but for plain sh instead:

```

$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2008-06-19 04:21 /bin/sh -> dash
$ ls -l /bin/bash
-rwxr-xr-x 1 root root 702160 2008-05-12 15:33 /bin/bash

```

---

