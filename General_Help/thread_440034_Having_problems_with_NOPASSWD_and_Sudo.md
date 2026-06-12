---
title: "Having problems with NOPASSWD and Sudo"
date: 2007-05-11
forum: General Help
---

### Post by Memory.Dump on 2007-05-11
I am trying to start a daemon up for my g15 Keyboard

the Daemon is called g15daemon....I have followed all the instructions I can find on this and while the daemon will run when I sudo it I always need to enter a pw after so I can't get it to start from my x sessions area I have edited my visudo and it currently looks like

 ```
NU nano 2.0.2                                     File: /etc/sudoers.tmp                                                                                  

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn,env_reset,env_keep+= " DISPLAY HOME XAUTHORIZATION "

# User privilege specification
root    ALL=(ALL) ALL
user    ALL=NOPASSWD: /usr/sbin/g15daemon

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

I'm not sure what else to do, any help would be appreciated

---

### Post by Memory.Dump on 2007-05-11
anybody out there have any ideas

---

### Post by NilsE on 2007-05-11
Seems like you were a little anxious by bumping this after 16 minutes so I will take a shot ant answering it

First off where you put "user" I think it should be your user ID

I am not sure about the deamon needing to be fully qualified but should work.

---

### Post by Memory.Dump on 2007-05-15
ok I changed the user to my name...and tried tried it but I still need to type in the pw

---

### Post by canatella on 2007-05-31
I had the same problem. If your "user" user is in the admin group, the line
%admin ALL=(ALL) ALL overrides your user line. Remove that line or change it to
%admin ALL=(ALL) NOPASSWD: ALL (of course, all user in the admin group won't have to enter their password anymore).

---

