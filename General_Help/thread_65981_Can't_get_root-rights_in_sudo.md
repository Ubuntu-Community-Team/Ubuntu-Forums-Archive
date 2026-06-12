---
title: "Can't get root-rights in sudo"
date: 2005-09-15
forum: General Help
---

### Post by Sethiano on 2005-09-15
Hi, I have tried to get root-access trough sudo, but It does not work.
Every time when I try to open a application that requires root-access a error-message pops up.
The message says something like: "Child process terminated with 1 status"

What to do?

It is the user "master" that I want to give full root-user rights

This is what my sudoers file looks like:
----------------------------------------------------------------------------------------------------

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

master ALL=(ALL) ALL
------------------------------------------------------------------------------------------ ](*,)

---

### Post by agm642 on 2005-09-15
Try adding "master" to the "admin" group, or putting "master ALL=(ALL) ALL" under "root "ALL=(ALL) ALL"

---

### Post by mlomker on 2005-09-15
> "Child process terminated with 1 status"

What to do?


Get the exact error message and search on here and on Google.  Your sudoer file looks fine.

---

### Post by mlomker on 2005-09-15
[QUOTE=agm642]Try adding "master" to the "admin" group, or putting "master ALL=(ALL) ALL" under "root "ALL=(ALL) ALL"[/QUOTE]

Won't matter.  Groups are just prefixed with an %.

---

### Post by agm642 on 2005-09-15
Yes, you're right, it was my fault.

---

### Post by Sethiano on 2005-09-15
I have tried all of that but nothing works :'(

---

### Post by mlomker on 2005-09-16
[QUOTE=Sethiano]I have tried all of that but nothing works :'([/QUOTE]

You still haven't posted the exact error message!  It's impossible for people to help you if you do not provide detailed information about the problem.

Have you verified that the 'master' account is in the **admin** group?  Normally that is the default setting and what grants sudo permissions.

Can you **su** to root in a terminal rather than using sudo?

---

