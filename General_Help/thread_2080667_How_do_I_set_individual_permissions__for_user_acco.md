---
title: "How do I set individual permissions  for user accounts?"
date: 2012-11-04
forum: General Help
---

### Post by dizzylizard on 2012-11-04
ATTN Mods or Admins: Please move this thread to the appropriate forums, as I couldn't figure out where my question belongs.

I haven't installed for anyone since Ubuntu 9.04, which gave an admin a lot of control over the permissions of each user account. I'm setting up 12.04 for a friend who is linux-dumb and want to be able to give him permission to install from the software center, but limit his ability to change anything in the system.  Unfortunately, 12.04 seems to only allow you to choose between a standard user and an administrator...is there any way to change individual permissions for the account from terminal (or a package to do it)?  

What I want to let him do:
Download and install games, apps, etc to the computer.
Access printers and peripherals.
Change settings in his own desktop to personalize it
shutdown the box

What I don't want him to be able to do:
Change user permissions
Create new user accounts
use the terminal for ANYTHING
access other users files
or basically, screw up anything I've spent three days setting up...

Any suggestions?

---

### Post by Cheesemill on 2012-11-04
Setting up the user as a standard user will achieve all of that except the following:
> use the terminal for ANYTHINGI don't see why this is a problem, a standard user can only use the terminal to run commands that affect files in their home directory anyway. If they can't use sudo then they can't mess anything up.


> access other users filesSet the permissions on everyones home directories so that only they have access:
```
sudo chmod 700 /home/*
```


> Download and install games, apps, etc to the computer.You can change the policykit settings so that ***any*** user can install software without needing a password. Please be aware that this will also enable any user to remove software as well. To do this you need to edit the file /usr/share/polkit-1/actions/org.debian.apt.policy and edit the following line (highlighted in red).
```
<action id="org.debian.apt.install-or-remove-packages">
  <description gettext-domain="aptdaemon">Install or remove packages</description>
  <message gettext-domain="aptdaemon">To install or remove software, you need to authenticate.</message>
  <defaults>
    <allow_any>auth_admin</allow_any>
    <allow_inactive>auth_admin</allow_inactive>
    <allow_active>auth_admin_keep</allow_active>
  </defaults>
</action>
``````
<action id="org.debian.apt.install-or-remove-packages">
  <description gettext-domain="aptdaemon">Install or remove packages</description>
  <message gettext-domain="aptdaemon">To install or remove software, you need to authenticate.</message>
  <defaults>
    <allow_any>auth_admin</allow_any>
    <allow_inactive>auth_admin</allow_inactive>
[COLOR=Red]    <allow_active>yes</allow_active>[/COLOR]
  </defaults>
</action>
```

---

