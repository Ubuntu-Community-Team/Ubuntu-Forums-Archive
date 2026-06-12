---
title: "Help! won't accept root password!"
date: 2007-10-06
forum: General Help
---

### Post by itlarson on 2007-10-06
My system has suddenly stopped accepting my root password-  this includes adept, sudo and other configuration tools.  How can I fix this?

---

### Post by bapoumba on 2007-10-06
What is the output to **groups**?

---

### Post by itlarson on 2007-10-06
two further questions- 
   -Why doesn't su work in Kubuntu?  Annoying to keep having to type sudo.
   -How do you change the root password anyway?

---

### Post by itlarson on 2007-10-06
juke dialout cdrom floppy audio video plugdev scanner lpadmin

-thanks for the quick reply!

---

### Post by bapoumba on 2007-10-06
From the grub menu, boot in recovery mode. You'll be root with a # prompt:
```
# adduser <your_login_here> admin
# reboot
```
You should be fine.

For the other questions: Ubuntu decided to use sudo instead of the root account:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")
5there are very little cases a regular user needs a root account).

To get a root shell:
```
sudo -i
```
Do not forget to **exit**.

---

### Post by itlarson on 2007-10-06
More weirdness-  
  First - I attempted to change the root password a week ago by using "sudo passwd".   The new password didn't take-  I still had to use the old one for adept or sudo.  Yesterday this stopped working.  I couldn't get root access under either password.  Just now I booted in recovery mode and tried the second (changed) password, and it worked.  When I started kde as a normal user, though,  I still couldn't get adept to accept either password.
   About the instructions You gave me-  I am a bit confused,  It looks like you are having me create a new user-  but I can't find "admin"  in the adduser man file and am not sure what this would do.

---

### Post by bapoumba on 2007-10-06
> **itlarson said:**
> 
   About the instructions You gave me-  I am a bit confused,  It looks like you are having me create a new user-  but I can't find "admin"  in the adduser man file and am not sure what this would do.
From man adduser:
 ```
Add an existing user to an existing group
       If  called  with two non-option arguments, adduser will add an existing
       user to an existing group.

```
For a user to have admin privileges on Ubuntu, it has to be in the admin group.
```
isabella@yeti:~ $ groups
isabella adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin
```

the /etc/sudoers file should look like this:```

isabella@yeti:~ $ sudo cat /etc/sudoers
[sudo] password for isabella:
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
[http://linux.die.net/man/5/sudoers]("http://linux.die.net/man/5/sudoers")

---

### Post by itlarson on 2007-10-06
/etc/sudoers is as you show it.  I added both my users to admin in /etc/groups, (one of them already was) but still no success.

---

### Post by bapoumba on 2007-10-06
> **itlarson said:**
> /etc/sudoers is as you show it.  I added both my users to admin in /etc/groups, (one of them already was) but still no success.

What is the output to:
```
sudo aptitude update
gksudo gedit
```

---

### Post by itlarson on 2007-10-06
logged in as root in rescue mode:
-the first line returns a list of packages and an error message about signatures, with a recommendation to run apt-get update
-the second line gave a message that gksudo is not installed, so I installed it with apt-get.  I then rebooted and logged in to kde as a normal user.  gksudo gedit popped up the root password dialog, but when I entered the password (which works fine in rescue mode) It just said incorrect password, as it has all day.

---

