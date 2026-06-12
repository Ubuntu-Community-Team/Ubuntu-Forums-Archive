---
title: "sudo -i command dont work"
date: 2007-11-29
forum: General Help
---

### Post by vikrant chaudhary on 2007-11-29
I installed Ubuntu 7.10 32 bit server edition on my dell machine.
I logged in with my user name and run sudo -i command. it's work fine. It change me to root login and I can run administrative commands.

It was working fine, I was running my own developed service, mean while due to some error, I was unable to close the service, so I have restart the machine.

Next time I logged in with my user name and run sudo -i command.
It doesn't change me to root login and I am unable to run administrative commands.

Is there a fix for this problem?

---

### Post by mpierce on 2007-11-29
Hmmm... strange problem! Can you sudo anything? 
If so, edit the file, /etc/sudoers and change all mpierce to your username. This will allow you to always become sudo without entering password. If you can't can you reinstall the sudo package?

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
%mpierce ALL=(ALL) NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
%mpierce ALL=(ALL) NOPASSWD: ALL

Hope this helps...

---

### Post by vikrant chaudhary on 2007-12-03
Unfortunately i m not able to run any sudo command, as well as i am not able to edit /etc/sudoers file. Even I am not able to run apt-get install sudo.

---

### Post by zvacet on 2007-12-03
Boot in recovery mode and type

```
adduser username admin
```

Of course username is **your** username

---

