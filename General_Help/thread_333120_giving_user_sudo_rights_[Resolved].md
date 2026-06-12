---
title: "giving user sudo rights [Resolved]"
date: 2007-01-06
forum: General Help
---

### Post by goneskiing on 2007-01-06
I've just upgraded to Edgy - I need to give a user sudo rights - I used the User Manager and checked Admin and changed the group to Admin - but the user cannot use Sudo - is this a bug ?  Is there something else missing ?

---

### Post by taurus on 2007-01-06
You need to add that user to both groups adm & admin in /etc/group.

---

### Post by aysiu on 2007-01-07
```
sudo adduser *username* admin
``` should do it. Make sure your /etc/sudoers file looks like this: ```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# User privilege specification
root ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
``` You use the command ```
sudo visudo
``` to edit the /etc/sudoers file.

---

### Post by goneskiing on 2007-01-07
thks for quick reply.  Actually I had to reboot  and that did it - merely switching users did not activate the change.  (I guess there is probably a restart service that can be run instead of rebooting but don't know what it is).

---

