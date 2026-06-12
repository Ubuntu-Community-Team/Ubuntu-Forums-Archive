---
title: "Compile xchat 2.8.0 with tcl"
date: 2007-01-11
forum: General Help
---

### Post by MarzioDance on 2007-01-11
What do I need to have tcl install into xchat when I compile it.

Here's the output  of configure:

xchat 2.8.0

Building GTK+ Interface .... : yes
Building TEXT Interface .... : no

PLUGINS: Perl: yes Python: yes TCL: no

mmx tinting ......... : yes     spelling .............. : static
XShm tinting ........ : no      plugin interface ...... : yes
text backend ........ : pango   nls/gettext ........... : yes
openssl support ..... : yes     ipv6 support .......... : no
dbus support ........ : yes     msproxy ntlm (ISA) .. : no

The binary will be installed in /usr/local/bin

Thanks for all the help

---

### Post by cbaumann on 2007-01-15
Hey,

I suggest you use your package manager to install tcl/tk.

Regards,

---

### Post by MarzioDance on 2007-01-20
Solved....
 
to configure use this command : ./configure --enable-tcl=/usr/lib/tcl8.4

and that should do it

---

