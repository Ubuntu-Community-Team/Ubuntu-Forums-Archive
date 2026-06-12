---
title: "need help fixing sudo command! [Resolved]"
date: 2007-01-19
forum: General Help
---

### Post by cd1680 on 2007-01-19
Hi I was trying to install logitech g15 drivers and I had to use the command sudo visudo and edit the file. However, I think I made a mistake and now I can't use sudo at all. I can't update my software and it gives this error message:
[B]
Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '48234499' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpLO0YEN' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/B]

What I changed in visudo is one line at the end. I changed the last line into **user ALL= NOPASSWD: /usr/local/sbin/g15daemon**. Is there any way to fix this?

---

### Post by taurus on 2007-01-19
Boot into recovery mode and change your /etc/sudoers back to this.

```
visudo
```

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by cd1680 on 2007-01-19
thank you so much!

---

### Post by taurus on 2007-01-19
So, sudo is back to what it is now.

---

