---
title: "sudo broken on 6.06 LTS"
date: 2007-03-28
forum: General Help
---

### Post by acormack on 2007-03-28
I have managed to break sudo on my kubuntu 6.06 LTS laptop and I can't work out what the problem is.

I can no longer sudo as any user other than root.  If I try this as user "myuser" then as soon as I type sudo l get a line appended to /var/log/auth.log saying

**Mar 28 18:57:42 localhost sudo: (pam_unix) auth could not identify password for [myuser]**

This is even before I type in the password!  (it behaves the same for all users other than root)

I assumed I had somehow corrupted /etc/sudoers .  Even adding mysuser specifically (as well as being in the admin group) made no difference.

I also tried re-installing the sudo package and that made no difference.

Please can anyone help me


Thanks in Advance 


Alec
===============================================================
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
myuser     ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
===============================================================

---

### Post by acormack on 2007-03-31
bump!

---

### Post by hikaricore on 2007-03-31
Did you edit the sudoers file directly?  Or did you originally run:

```
sudo visudo
```

---

### Post by acormack on 2007-03-31
I may have originally edited it using vi directly - but I have since definitely used visudo

Is there a way I can recreate the default file from scratch?

I seem to remember the problem happened after I had been trying to set up Active Directory authentication so it may be more of a problem in pam than /etc/sudoers.

---

