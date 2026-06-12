---
title: "start vpnc using sudo"
date: 2006-08-28
forum: General Help
---

### Post by RikoW on 2006-08-28
Hi everybody,

this should be simple and straight forward, but I can't figure it out.

I connect via vpnc to our organizations intranet. However, I need to use sudo to establish the connection. So, to make my life easier, I added the vpnc commands to the sudoers file (of course using viudo):

```

Cmnd_Alias VPNC = /usr/sbin/vpnc, /usr/sbin/vpnc-connect, /usr/sbin/vpnc-disconnect
wichmann ALL=NOPASSWD:VPNC
```

expecting, not be be asked for the password anymore when I do:

```
> sudo vpnc-connect my_profile
Password:

```

Unfortunately, as you see above, I'm still asked. What am I missing?

Thanks,

            Riko

---

### Post by RikoW on 2006-08-29
Apparently, setting the user privileges have to be at the end of the sudoers file to work as expected:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias VPNC = /usr/sbin/vpnc, /usr/sbin/vpnc-connect, /usr/sbin/vpnc-disconnect


# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL


# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# enter user privileges here!!
# ----------------------------
wichmann ALL = NOPASSWD: VPNC

```

Cheers,

             Riko

---

