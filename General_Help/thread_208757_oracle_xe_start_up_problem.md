---
title: "oracle xe start up problem"
date: 2006-07-04
forum: General Help
---

### Post by faziz on 2006-07-04
hi guyz

i ve just installed oracle xe and followed the instructions of creating swap file and all that very closely. In the end oracle xe installed perfectly and even started off very nicely. i managed to create new users and allowed http acces to the web based administrative application. but after restart of the system i cant restart the oracle server and getting following error.

root@faziz:/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/config/scripts# ./startdb.sh
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xsetroot:  unable to open display ':0'
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Warning: This program is an suid-root program or is being run by the root user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %s
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xsetroot:  unable to open display ':0'

i ll appreciate any help.

---

