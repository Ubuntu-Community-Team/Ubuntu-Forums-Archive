---
title: "Disabling sudo password"
date: 2006-07-26
forum: General Help
---

### Post by glinsvad on 2006-07-26
I've been browsing the Unofficial Ubuntu Guide and came across the thread
[How to use sudo without prompt for password]("http://ubuntuguide.org/wiki/Dapper#How_to_use_.22sudo.22_without_prompt_for_password_.28not_secure.29"). I tried but it didn't work or I misunderstood something. (Actually I thought it worked, but then I remembered that sudo keeps the password untill you do sudo -K, then it promts again the next time)

> 
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

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL


So far I've tried changing the root-line to:
> 
root ALL=(ALL) NOPASSWD: ALL

and
> 
root ALL=NOPASSWD: ALL



Then I tried using my username glinsvad leaving the root-line as original:
> 
glinsvad ALL=(ALL) NOPASSWD: ALL

and
> 
glinsvad ALL=NOPASSWD: ALL


Finally I tried combinations of changing and adding these lines, but that didn't work either.

Do you know what's wrong?

---

### Post by jordilin on 2006-07-26
I don't know what the guide you point out says, but if you take a look at the official wiki, in:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
it works for sure.

---

### Post by glinsvad on 2006-07-26
> **jordilin said:**
> I don't know what the guide you point out says, but if you take a look at the official wiki, in:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
it works for sure.

Thanks, but that did not tell me anything I didn't know already. I'm trying to setup my system so certain users, e.g. system administrators, don't have to type in the password everytime they run a sudo-command.

Anyway, the title of my link says it all. I want to get rid of the password promt when sudo is run...

---

### Post by glinsvad on 2006-07-26
Ok, finally figured it out. Well, almost.

It seems the %admin-line if the place to add "NOPASSWD:" otherwise the setting is overridden by the lines below it.
> 
%admin ALL=(ALL) NOPASSWD: ALL


Alternatively I've found that adding user-lines must be done below the other lines (as explained).
> 
glinsvad ALL=(ALL) NOPASSWD: ALL


As usual the [Sudoers Manual]("http://www.courtesan.com/sudo/man/sudoers.html") was the key - RTFM once again *sigh*

---

