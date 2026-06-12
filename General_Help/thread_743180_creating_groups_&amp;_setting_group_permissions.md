---
title: "creating groups &amp; setting group permissions"
date: 2008-04-02
forum: General Help
---

### Post by Th3Professor on 2008-04-02
Re: "groupadd" and "addgroup"... and...
usermod -G groupname username
and
adduser user group
...

How do I "define" what access/permissions a group has?

Is it set within a file in /etc?

I would like to do this via console.

It seems that when creating a group you'd assign what privileges it has (before adding users to the group).

If someone would like a specific example of what I'm trying to do, please ask, or if it doesn't require that and the generic question here is good enough, cool beans. :) At present, I am more interested in actual groups, like their functions, than plugging users into them.

Thanks!

---

### Post by logos34 on 2008-04-02
This should answer your questions:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

---

### Post by bodhi.zazen on 2008-04-02
I think permissions are set file by file, directory by directory and not by editing group permissions in the way you conceptualize.

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Th3Professor on 2008-04-02
This is the case I'm looking at:

Running a MUSH (MUD or MU*) server.

Wanting to set up 2 custom instances of the "restart" command.

1. Automatic restart.
Perhaps using a script & crontab, checking for the mu* server possibly being offline and automatically invoking the restart command.

2. Manual restart.
Giving restrictive access to specific users so that they can restart the mu* server on their own in the event that it goes down and the auto-restart hasn't checked/acted yet.

In one regard, for manual restart, this is going off the assumption that user jdoe, for example, already has generic user SSH access. So, there's no immediate need for bothering with creating specialized subdomains geared towards logging in for specific mu*-related access.

I tried making a copy of the "restart" command, creating a hard link (symbolic link had a problem with chgrp) of that "restart" command within a freshly created directory, did the various chgrp, chmod, etc. - and groupadd, etc. options - and tested it by logging into something like "jdoe" (and group privs, etc. were given to jdoe), though it didn't work. The link and copy of the link in a separate directory, with proper rwx sets, is to protect the original file and original directory.

Basically, how can one set up a secure means of giving specific users restrictive access to "restart" the mu*?

This is all regarding instance "2." (manual restart). If there is a really cool script floating around somewhere that could be modified to fit with instance "1." (automatic restart), that'd be one uber-cool-beans to go! :)

---

### Post by bodhi.zazen on 2008-04-02
You can do this via sudo. That is what is so cool about sudo vs su. su is all or none, but wudo can be configured to allow root access to as many or few commands as needed.

[http://www.debian-administration.org/articles/33](http://www.debian-administration.org/articles/33)

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html)
[http://www.unixcities.com/sudo/index.html](http://www.unixcities.com/sudo/index.html)

Use sudo visudo to configure sudo (/etc/sudoers)

---

### Post by Th3Professor on 2008-04-02
I'd like to use a non-sudo and non-su approach.

---

