---
title: "Removing the need to be root for x command"
date: 2007-03-30
forum: General Help
---

### Post by zergberg on 2007-03-30
Is there any way I can make a command executable without me being root or using sudo?

For example, I'd just have to type 'shutdown -h 0' instead of 'sudo shutdown -h 0'.

---

### Post by aysiu on 2007-03-30
Is it the password that bothers you, or the extra five key strokes?

---

### Post by hikaricore on 2007-03-30
> **zergberg said:**
> Is there any way I can make a command executable without me being root or using sudo?

For example, I'd just have to type 'shutdown -h 0' instead of 'sudo shutdown -h 0'.

Well don't quote me on this, but I suppose you could make an alias in ~/.bashrc

```
alias shutdown0='sudo shutdown -h 0'
```

Then edit your sudoers file:

```
sudo visudo
```

and add:

```
yourusername ALL=NOPASSWD: /sbin/shutdown
```

Then you should be able to type:

```
shutdown0
```

To shutdown with your specified params.

(I guess this could be somewhat of a security risk, but I doubt that matters much)

---

### Post by josephus on 2007-03-30
somewhat off-topic, but how does shutdown know that it needs to be root to shutdown.  Is there a file somewhere that stores all the information of which operations require root?

*edit:  guess it was a stupid question, since every file has the permissions bit associated with them*

---

### Post by kerry_s on 2007-03-30
You can create a "shutdown" group and only add users you want to be able to shutdown.

sudo visudo

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

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%shutdown ALL=NOPASSWD: /sbin/reboot
%shutdown ALL=NOPASSWD: /sbin/shutdown 


```

Then just go into the users and group app, create a group "shutdown" and add the users you want to shutdown the computer to that group.
In case your running a custom install and don't have a users & group app, you can edit the /etc/group file and just manually add it, which is what i do in fluxbox.

---

