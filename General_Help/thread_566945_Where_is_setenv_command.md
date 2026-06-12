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


B.R.
satimis

---

### Post by FFred on 2007-10-04
Setenv is part of the C shell. Ubuntu uses Bash by default. 
You'd have to edit your user to make it use the C shell if you want to use setenv. There is no such standalone command.

---

### Post by girishv on 2007-10-04
You can use export in place of setenv in bash. There is a small change in the syntax

setenv HELLO "echo hello world"    csh/tcsh
export HELLO="echo hello world"   bash

The quotes are needed only if you are using more than one word ..

Secondly, you dont have to set the display environment specifically when you are using ssh. Run ssh with -X flag to enable X11 forwarding


ssh -X guest@local_ip



Girish

---

### Post by satimis on 2007-10-04
> **FFred said:**
> Setenv is part of the C shell. Ubuntu uses Bash by default. 
You'd have to edit your user to make it use the C shell if you want to use setenv. There is no such standalone command.
Noted with thanks.

---

### Post by satimis on 2007-10-04
Hi girishv;


Thanks for your advice.

> 
You can use export in place of setenv in bash. There is a small change in the syntax

setenv HELLO "echo hello world"    csh/tcsh
export HELLO="echo hello world"   bash

The quotes are needed only if you are using more than one word ..

On desktop:-

$ xhost 192.168.0.10
192.168.0.10 being added to access control list

$ ssh 192.168.0.10
satimis@192.168.0.10's password

then server connected

$ export DISPLAY="192.168.0.11:10.0"
No complaint

$ xterm```

xterm Xt error: Can't open display: 192.168.0.11:10.0

```

> 
Secondly, you dont have to set the display environment specifically when you are using ssh. Run ssh with -X flag to enable X11 forwarding

ssh -X guest@local_ip

I tried more than 2 days reading many doc on Internet w/o a solution.

sever -> desktop
both scp and ssh works w/o problem with X forwarded.

desktop -> server
scp works w/o problem
ssh only works on connection but w/o X forwarded.

Warnings are;```

Gdk-warning **: locale not supported by C library

Gtk-warning **: Locale not supported by C library
             using the fallback 'C' locale

```

```

Gtk-Warning ** cannot open display:

```


I'm still struggling for a solution.


B.R.
satimis




Girish[/QUOTE]

---

