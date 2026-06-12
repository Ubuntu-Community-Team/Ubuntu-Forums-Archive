---
title: "System does not prompt for root password at all!!! [Resolved]"
date: 2006-12-24
forum: General Help
---

### Post by Portable_Jim on 2006-12-24
I have just discovered that my system does not prompt for root password at all. I changes root password - not needing any password. Still no password prompt.

PLEASE HELP!!!!!!!!!!!!!!!!!

---

### Post by Jussi Kukkonen on 2006-12-24
You used sudo, right? This is what *man sudo* says:
>        Once a user
       has been authenticated, a timestamp is updated and the user may then
       use sudo without a password for a short period of time (15 minutes
       unless overridden in sudoers).

If this wasn't the case, you might want to give some more details, like whether you are really using a root password or the sudo system.

---

### Post by Portable_Jim on 2006-12-24
I have never been asked for root password since login - but I can open synaptic no problem - no dialog boxes.
I then went and put me out of the admin group. I prompted for the password  and I put my own in. Now cannot run administrative applications.

---

### Post by Portable_Jim on 2006-12-24
Please HELP!!!

---

### Post by po0f on 2006-12-24
Portable_Jim,

Boot in recovery mode.  Re-add your user to the 'admin' group:
```
[FONT="Courier New"]# gpasswd -a <user_name> admin[/FONT]
```

---

### Post by Olav on 2006-12-24
You should have just left everything like it was... The root user in Ubuntu per default does not have a password, so you cannot login as that user. With yourself in the admin group you can use sudo to do administrative tasks. It will ask you for a password, but it does remember that password for a little while. Perhaps that's why you were able to open Synaptic without a password, you may have already given your password a few minutes before opening the program.

Now that you have taken yourself out of that group, and not having set a root password, I'm not at all sure how you would gain root access again.

---

### Post by Olav on 2006-12-24
> **po0f said:**
> Portable_Jim,

Boot in recovery mode.  Re-add your user to the 'admin' group:
```
[FONT="Courier New"]# gpasswd -a <user_name> admin[/FONT]
```

Ah yes, sounds right.

---

### Post by Portable_Jim on 2006-12-24
Leaving everything as it was meant that (I think) anything could acess and change any part of my computer.

I had planned of doing:
1. login as root (command line) or ```
su root
```2. ```
users-admin
```I will try what you suggested:
[FONT=Courier New]```
gpasswd -a <user_name> admin
```[/FONT]

---

### Post by Olav on 2006-12-25
> **Portable_Jim said:**
> Leaving everything as it was meant that (I think) anything could acess and change any part of my computer.
I am quite sure that is not true. Only the first user created during the Ubuntu installation gets added automatically to the admin group. Only that user is then able to use sudo. This is quite secure.

For other reasons I do configure a password for root each time I set up an Ubuntu box. It's as simple as "sudo passwd".

---

### Post by Vox754 on 2006-12-25
[QUOTE="Olav"]I am quite sure that is not true. Only the first user created during the Ubuntu installation gets added automatically to the admin group. Only that user is then able to use sudo. This is quite secure.[/QUOTE]
Yeah, then, if you do not want to *accidentally* have acces to "sudo", you should create *another* user, and put this one **out** the "admin" group.

Then you would have another level of security:
  root (not enabled)
  user1 (can access "sudo")
  user2 (cannot access "sudo")

---

### Post by aysiu on 2006-12-25
I think you should read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by Portable_Jim on 2006-12-26
**Problem solved: Fresh Edgy install.**

I got a Hard drive for CHRISTmas and wanted an upgrade to Edgy. So I did a fresh install of edgy. The upgrade Fixed previous problems of my broken system:
[http://www.ubuntuforums.org/showthread.php?t=310043](http://www.ubuntuforums.org/showthread.php?t=310043)
[http://www.ubuntuforums.org/showthread.php?t=319580](http://www.ubuntuforums.org/showthread.php?t=319580)
[http://www.ubuntuforums.org/showthread.php?t=303269](http://www.ubuntuforums.org/showthread.php?t=303269)

Anyone Know how to set the timeout for the root password? (How long before you have to re-enter the password).

---

### Post by aysiu on 2006-12-27
> **Portable_Jim said:**
> **Problem solved: Fresh Edgy install.**

I got a Hard drive for CHRISTmas and wanted an upgrade to Edgy. So I did a fresh install of edgy. The upgrade Fixed previous problems of my broken system:
[http://www.ubuntuforums.org/showthread.php?t=310043](http://www.ubuntuforums.org/showthread.php?t=310043)
[http://www.ubuntuforums.org/showthread.php?t=319580](http://www.ubuntuforums.org/showthread.php?t=319580)
[http://www.ubuntuforums.org/showthread.php?t=303269](http://www.ubuntuforums.org/showthread.php?t=303269)

Anyone Know how to set the timeout for the root password? (How long before you have to re-enter the password).
Try this:
[http://doc.gwos.org/index.php/Change_default_timeout_in_sudo](http://doc.gwos.org/index.php/Change_default_timeout_in_sudo)

---

### Post by Portable_Jim on 2006-12-27
> **aysiu said:**
> Try this:
[http://doc.gwos.org/index.php/Change_default_timeout_in_sudo](http://doc.gwos.org/index.php/Change_default_timeout_in_sudo)
Thanks aysui!

(P.S Could you please put " [Resolved]" at the end of this thread's title. Although I can mark it as resolved,  I cannot change the title. - Pleae reply via PM so it does not bump the thread again)

---

