---
title: "sudo segmentation fault"
date: 2008-06-05
forum: General Help
---

### Post by darbid on 2008-06-05
Here is what I get

```
wg@wg-server:~$ sudo nautilus
[sudo] password for wg: 
seahorse nautilus module initialized
Initializing nautilus-share extension
Segmentation fault
```

or when I try to open up a file with sudo gedit if get a segmentation fault too.

What is the problem?

---

### Post by robjoski on 2008-06-05
Have you tried using gksudo instead of sudo?
Instead of having to type in your password in the terminal, you type it in in a "window".
That's what you're supposed to do for graphical applications - it's more secure.

---

### Post by krlhc8 on 2008-06-05
Crap that sucks!  I've been scouring the internet, trying to find a vestige of a solution for you.  I know that segmentation faults occur when memory is trying to be accessed from applications that don't have correct permissions.  So it seems like you have your permissions all messed up.  Did this just start happening?  Maybe try accessing synaptic package manager and clicking "mark all upgrades" then apply.  Can you do anything as root?  Are you a 64-bit user or what?

---

### Post by darbid on 2008-06-05
yeh i am not sure gksudo does much, atleast not for me.

There is nothing to update.

I have just installed an external eSATA Hard Drive 1TB.  And formated it.

I was trying to share it when I realised that sudo would not work.

It is only 32.

I am a beginner.

Thanks so much guys for helping.

---

### Post by Kernel_Krunch on 2008-06-05
Yes i get problems with sudo gedit aswell

I went old school and installed mc :)  then sudo mc for system work.

---

### Post by darbid on 2008-06-09
bump - any one else going to have a go here please?????

---

### Post by krlhc8 on 2008-06-09
You must not have installed Ubuntu correctly for root priveleges.  In Debian and Ubuntu, you can have certain users use sudo while others can't (probably you right now).  Try logging in as "admin" and take a look at your /etc/sudoers file (if you can access it somehow as root).  This file determines who uses sudo.  Here's my file:

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```


Try adding the following in red: 
```

root     ALL=(ALL) ALL
[COLOR="Red"]wg	ALL=(ALL) ALL[/COLOR]

```

This really should work.

---

### Post by darbid on 2008-06-09
Thanks for writing a suggestion

that is not a problem to do with

sudo visudo

So I put there what you suggested but it did not change anything.

---

### Post by krlhc8 on 2008-06-09
Out on a limb here, but try reinstalling sudo in the synaptic package manager.

---

### Post by darbid on 2008-06-10
That Limb did not work either.

Isn´t this fault to do with a drive or software that is not saved right or in the wrong place?

Is there not a log file somewhere?

---

### Post by krlhc8 on 2008-06-10
How did you install Ubuntu?  Did you do the simple installation or advanced?  If "advanced," then I would recommend backing up your main files and using the simple reinstallation.  I wish I knew a less barbaric solution.

---

### Post by kimstebel on 2008-07-23
nautilus has a bug that makes it crash when an empty dvd is in your drive and you run it with sudo. is that the case??
i don't know about gedit though.
if you haven't modified system internals that could break sudo or gedit, you should file a bug report.
have you tried using su instead?
set a root password with sudo passwd and then simply do:
su
gedit

---

### Post by papafreebird on 2008-10-21
> **kimstebel said:**
> nautilus has a bug that makes it crash when an empty dvd is in your drive and you run it with sudo. is that the case??


Sorry for digging up an old topic but I just had to say thank you for that.  I've been looking for an answer to why I was getting segmentation fault using sudo.  That was the reason.

---

