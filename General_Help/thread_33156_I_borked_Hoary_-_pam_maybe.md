---
title: "I borked Hoary - pam maybe?"
date: 2005-05-09
forum: General Help
---

### Post by reid on 2005-05-09
I added the Ubuntu HArdened Security-Enhanced Linux repository.
Sometime later I got notification from the Ubuntu update manager that there were updates and I installed them. These were:
sysvinit to 2.86-5ubuntu7
libsepol1 (1.4-2)
coreutils to 5.2.1-2ubuntu1
cron to 3.0pl1-86ubuntu2
libpam-modules to 0.78-2
libpam-runtime to 0.78-2
libpam0g to 0.78-2
libpam0g-dev to 0.78-2
libselinux to 1.22-2
logrotate to 3.7-3
openssh-client to 1:3.9p1-1ubuntu3

I started getting pam errors (I don't remember exactly what they said) when I tried to go into synaptic, or sudo. ](*,) 
I decided to reboot and see if that fixed my problem.
Now I can not log in from the console or in GDM as root or my regular user.  I enter my user name and it does not even prompt for a password, just says 'Login incorrect' in console and 'Authentication failed' in gdm.
I can get in as root if I go into 'Recovery mode' from the grub menu.

Is there some setting that is messed up?
I hope this is an easy fix.

Thanks for any help.

---

### Post by reid on 2005-05-10
[QUOTE=reid]I added the Ubuntu HArdened Security-Enhanced Linux repository.
Sometime later I got notification from the Ubuntu update manager that there were updates and I installed them. These were:
sysvinit to 2.86-5ubuntu7
libsepol1 (1.4-2)
coreutils to 5.2.1-2ubuntu1
cron to 3.0pl1-86ubuntu2
libpam-modules to 0.78-2
libpam-runtime to 0.78-2
libpam0g to 0.78-2
libpam0g-dev to 0.78-2
libselinux to 1.22-2
logrotate to 3.7-3
openssh-client to 1:3.9p1-1ubuntu3

I started getting pam errors (I don't remember exactly what they said) when I tried to go into synaptic, or sudo. ](*,) 
I decided to reboot and see if that fixed my problem.
Now I can not log in from the console or in GDM as root or my regular user.  I enter my user name and it does not even prompt for a password, just says 'Login incorrect' in console and 'Authentication failed' in gdm.
I can get in as root if I go into 'Recovery mode' from the grub menu.

Is there some setting that is messed up?
I hope this is an easy fix.

Thanks for any help.[/QUOTE]

RESOLVED  \\:D/ 
I had to fiddle with pam settings, and change access permissions.

---

