---
title: "The configuration could not be loaded / Permissions screwed"
date: 2008-05-16
forum: General Help
---

### Post by lordgreg on 2008-05-16
Hi everyone,

a bit of history: I tried to chmod a directory inside my home dir to 777. instead of typing . i accidentally typed / (meaning i've changed all dir permissions to 777. great, isn't it?).

i fixed the sudo command allready from recovery console so few things work again as they should, but lots still doesn't.

----

Here's my current problem, when i try to open "Network" settings through System > Administration, i receive  "The configuration could not be loaded" and "You are not allowed to access the system configuration" error. 

I've also went to Synaptic Package manager and deleted and installed again **gnome-system-tools** and **system-tools-backends**. 

Please tell me what else to do, to regain the access of those menus!


--

Also, samba shared public folder stopped working after the "sudo chmod" problem. All settings in smb.conf are perfectly fine, so no idea, what to change here? Permissions yes, but where?

Thank you for your help!

---

### Post by lordgreg on 2008-05-16
update:

i've reinstalled the dbus packages, now i can get into all the menus stated above (network settings, services settings etc), but new problem appeared:

all settings are disabled/locked.

i also checked if my username is in group "admin" and it is, so now, i really don't know what the problem is. even if i run the services-settings with sudo, it's still disabled.

help me out :$

---

### Post by chrisccoulson on 2008-05-16
Have you tried clicking the 'Unlock' button?

And doing a recursive chmod of / is a really bad idea. You'll probably struggle to get all the permissions back how they were, and you're likely to find lots of little things that don't work properly anymore. You'd be better off doing a re-install.

---

### Post by lordgreg on 2008-05-19
the unlock button does not work as it is disabled like others parts of the window. network connections window is NOT the only one acting like that. i also found a bash script, which changes all permissions to default (when you install ubuntu). so everything works as it should, only 2 problems i have, as stated:

1. network and few other options can be opened, but not configured, even if u start them through console with sudo or gksu.

2. samba shared folder doesn't work anymore, though the config file is the same or reconfigured as public, non-password protected etc etc.

and that's about it.. i don't want to start all over again with only 2 slightly harder problems i'm having.

any ideas anyone?

thank you!

---

### Post by chrisccoulson on 2008-05-19
Where was this bash script you found?

---

