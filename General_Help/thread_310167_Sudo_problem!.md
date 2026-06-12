---
title: "Sudo problem!"
date: 2006-11-30
forum: General Help
---

### Post by DRicher33 on 2006-11-30
Hi all,

Running Edgy and I'm being asked to enter my password twice using sudo

so if I run a command like sudo apt-get update it asks me for my password, which I enter, and then it asks again, which I enter again.  If I don't do it twice I get auth failed error.

Sorry if this is a newbie question.

---

### Post by taurus on 2006-11-30
What is the output of this command from a terminal, Applications -> Accessories -> Terminal?

```
groups
```

---

### Post by aysiu on 2006-11-30
No chance you have numlock on by accident or are mistyping your password?

---

### Post by bettlebrox on 2006-11-30
Did you make any changes to /etc/sudoers or /etc/pam.d/sudo ?

---

### Post by DRicher33 on 2006-12-05
Hi all,

Thanks for replying..the weekend kept me away from this server.

When I type groups I get:
<my user-name> adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

Aysiu--it's not a mistyped password..I have to enter the password twice like below:

<my user-name@<my host-name>:~$ sudo /etc/pam.d/sudo
Password:
Password:

In my /etc/pam.d/sudo I have:

#%PAM-1.0

@include common-auth
#@include common-account

Thanks for the help!

---

### Post by aysiu on 2006-12-05
Try [this](http://www.psychocats.net/ubuntu/sudo), and see if it makes a difference.

---

### Post by DRicher33 on 2006-12-05
No Joy.

That is exactly what my sudoers is programmed to.

---

### Post by DRicher33 on 2006-12-05
Could this have something to do with my problem?

In webmin I see this for logged in users

my name 	:0 	Nov 30 13:55 	Local
my name 	pts/0 	Dec 5 10:40 	:0.0

---

### Post by bettlebrox on 2006-12-05
Can you show /etc/sudoers?

---

### Post by DRicher33 on 2006-12-07
here is my sudoers:

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

---

### Post by wesley_of_course on 2006-12-13
Thank You - Thank You - Thank You !   Aysiu 

 I had the same problem and didn't realize Safe mode was ROOT , that website is AWESOME ! Thanks again !   

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

 May you find another go-cup under your tree !

---

