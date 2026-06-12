---
title: "Where is setenv command"
date: 2007-10-04
forum: General Help
---

### Post by satimis on 2007-10-04
Hi folks,


Ubuntu 7.04 desktop


I can't find the captioned command.  On Terminal

$ which setenv
No printout

# man setenv
No manual entry for setenv,.


I have tcsh and libextutilis_f77_perl installed.

On Terminal;

$ tcsh
ubuntu704:-> which setenv
setenv: shell built-in command.


I need to run following commands on Terminal;
$ xhost server_ip
$ ssh server_ip

( remark:
$ echo $DISPLAY (after connection - server)
localhost:10:0

$ echo $DISPLAY (local)
:0.0        )

$ setenv DISPLAY local_ip:10.0
$ xterm


I tried couple days unable to make server application displayed locally.  Server connected but X forwarding fails with warning;```

Gtk-Warning ** cannot open display:

```


Pleae advise.  TIA


Remark:
X11Forwarding yes


B.R.
satimis

---

