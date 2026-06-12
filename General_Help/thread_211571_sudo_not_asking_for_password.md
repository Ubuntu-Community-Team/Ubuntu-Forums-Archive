---
title: "sudo not asking for password"
date: 2006-07-08
forum: General Help
---

### Post by myrdos on 2006-07-08
I have a Kubuntu installation with a user named 'admin' for the primary user. I want to add user 'myrdos' to the list of sudoers. So I used sudo visudo and altered my /etc/sudoers.tmp file to look like this: > # /etc/sudoers
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

myrdos ALL=(ALL) ALLThe problem is that myrdos can use sudo without ever having to enter a password. sudo -K and sudo -k do nothing. This seems very insecure to me... does anyone have any suggestions?

---

### Post by tonyr on 2006-07-08
The usual way to do what you want is to add user **myrdos** to the group
**admin**, using **System->Administration->Users&Groups**, instead of
adding the user directly to **/etc/sudoers**.

---

### Post by mindwarp on 2006-07-08
I think the confusion exists here because in ubuntu there is a default group called "admin" that generally you would make myrdos a member of to use sudo.

---

### Post by myrdos on 2006-07-08
> I think the confusion exists here because in ubuntu there is a default group called "admin" that generally you would make myrdos a member of to use sudo.OK! That sounds like it must be the problem... I restored /etc/sudoers.tmp to it's original state, and added myrdos to group admin as per tonyr's instructions. However... I still have the same problem: myrdos doesn't need to enter a password to use sudo.

I wonder if the problem would be fixed if I renamed the admin user to something else? Or is there some special admin group that has been overwritten because I made an account with the same name, and is now gone forever?

---

### Post by tonyr on 2006-07-08
**Sudo** use has a password refresh timeout.  After the first **sudo** use, you
don't have to enter the password with subsequent uses unless you
haven't used it in the timeout period.  I think the default is
5 minutes, or something similarly short.  Are you sure you
are not running into this?  To check, open a new terminal and
try a **sudo** command.

---

### Post by myrdos on 2006-07-08
I'm very sure! Using a new terminal or typing sudo -k do nothing. I even rebooted with no effect.

---

### Post by c-yoborg on 2007-02-15
I got the same problem: added user via *kde system settings* - added to group *admin* - logged in as user -  never entered a password for sudo - *dontLikeIt*

---

### Post by c-yoborg on 2007-02-15
solved my problem: user was added to group *sudo* - removed user from group sudo in /etc/group

---

