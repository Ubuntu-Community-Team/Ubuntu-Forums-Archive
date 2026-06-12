---
title: "moved /lib folder"
date: 2007-08-20
forum: General Help
---

### Post by Jota1234 on 2007-08-20
I got a little careless with my wildcards and accidentally moved the /lib folder to the new location /usr/local/lib/lib

Of course, libraries like ld-linux.so.2 are not where they should be, and bash doesn't recognize most commands (like mv).

I tried the following (since sudo isn't recognized, and so editing /etc/ld.so.conf is out):

ldconfig -n /usr/local/lib/lib
/usr/local/lib/lib/ld-linux.so.2 --library-path /bin/ mv /usr/local/lib/lib /lib

but I get an error message:
mv: error while loading shared libraries: libacl.so.1: cannot open shared object file: No such file or directory

I'm out of ideas, so any help that doesn't involve reinstalling the OS would be most welcome.  I guess I'm lucky that I had a browser already open.

I'm running Ubuntu Dapper Drake 6.06

---

### Post by wj32 on 2007-08-20
use the livecd to move it back?

---

### Post by Spr0k3t on 2007-08-20
This is a perfect moment to use the livecd.

---

### Post by Jota1234 on 2007-08-20
I had never used a LiveCD before.  Incredibly handy.  Worked like a charm.

---

