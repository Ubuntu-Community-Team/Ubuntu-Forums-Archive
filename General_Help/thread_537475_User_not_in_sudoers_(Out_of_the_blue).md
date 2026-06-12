---
title: "User not in sudoers (Out of the blue)"
date: 2007-08-28
forum: General Help
---

### Post by flipjarg on 2007-08-28
For some reason sudo is not working for me. It worked fine yesterday but today it just stopped working. I think it started when I miss-typed the password a few times. I can use **su** and have had no problem running **visudo**. I've found a few posts on the forums here and a little on Google but nothing looks right yet.

I get the error:
> *userName*is not in the sudoers file.  This incident will be reported.

my /etc/sudoers: 
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

### Post by flipjarg on 2007-08-29
I thought I'd just give **dpkg-reconfigure sudo** a try. I did it and restarted...I thought it was good again... turns out it's not....

**[color=red]UPDATE:[/color]** I still haven't got any idea what created the problem but I found out how to fix it. Login and use **su** or login as root. Type **visudo** and under the part where it says root  ALL=(ALL) ALL type the following:

```
*userName* ALL=(ALL) PASSWD: ALL
```

---

### Post by PilotJLR on 2007-08-29
Given you previous sudoers file, anyone in the admin group should be able to sudo...

in /etc/group, is your username still listed in the admin group?

---

### Post by aysiu on 2007-08-29
Read this:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

It elaborates on what PilotJLR is talking about.

---

### Post by StarscreamD on 2007-12-31
Same issue here, was fixed due to this post. Can't thank you enough, forum options wouldn't allow me to thank! No Star icons.. hrm I am logged in. Oh well. Thanks again! :D

---

