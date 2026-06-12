---
title: "sudo problem."
date: 2005-05-16
forum: General Help
---

### Post by DaturaX on 2005-05-16
When i type sudo -s -H, it gives me this error.

dave@panther:~$ sudo -s -H
dave is not in the sudoers file.  This incident will be reported.

---

### Post by DaturaX on 2005-05-16
[QUOTE=DaturaX]When i type sudo -s -H, it gives me this error.

dave@panther:~$ sudo -s -H
dave is not in the sudoers file.  This incident will be reported.[/QUOTE]
 never mind. I got it working when i took a look at the /etc/sudoers file.

Thanks

---

### Post by bored2k on 2005-05-16
**edit -- ...**

Was dave user created after the ubuntu install?

you need to add him to the sudoers, wich is the sudo maintainer's files.

Type this inside a terminal session:
```

export EDITOR=gedit && sudo visudo

```
You will get something like

>     # sudoers file.
    #
    # This file MUST be edited with the 'visudo' command as root.
    #
    # See the man page for details on how to write a sudoers file.
    #

    # Host alias specification

    # User alias specification

    # Cmnd alias specification

    # Defaults

    Defaults    !lecture,tty_tickets

    # User privilege specification
    root    ALL=(ALL) ALL

    # Added by Ubuntu installer
    reb    ALL=(ALL) ALL
    dave    ALL=(ALL) ALL

---

