---
title: "NX Server Problem when installing.[SOLVED]"
date: 2007-01-30
forum: General Help
---

### Post by marko_4454 on 2007-01-30
Hello to you all, 
I am having this problem since a couple of days and I cant seem to find the solution. So, I can't install NX Server (from NoMachine, NOT Free NX) while I was able to install the node and the client perfectly.
[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

Here is what I get:

> 
Unpacking nxserver (from nxserver_2.1.0-17_i386.deb) ...
Setting up nxserver (2.1.0-17) ...
NX> 700 Installing: server at: Tue Jan 30 14:38:30 2007.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 ERROR: Output: useradd: group nx exists - if you want to add this user to that group, use -g..
NX> 700 ERROR: Cannot add user: nx to the system.
dpkg: error processing nxserver (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver


Does anyone have a clue? Any help at all would be really helpful. Thanks!

---

### Post by Brunellus on 2007-01-31
booting this to general support in the hopes that someone knows more about it than I do.

---

### Post by dannyboy79 on 2007-01-31
please post sudo aptitude show nxserver output. it looks to me that it is installed by reading the error message. all you have to do is add nx user to the nx group. just read the error and you'll be fine. is this a second or third attempt at installing this? if so, first do a sudo aptitude remove (and then remove and purge the client, node and server) then do a fresh install of them in the correct order. if during the removal of all of them, the nx user remains, then remove that user prior to installing again.

---

### Post by darrenm on 2007-01-31
Just do a groupdel nx then reinstall NX

---

### Post by dad311 on 2007-01-31
Yes, delete the nx group and nx user, then reinstall.

---

### Post by marko_4454 on 2007-01-31
Thank you to everyone. This is what the problem was: 
Well, there was this group "nx" (no user "nx", I had removed it already), I would delete it from the Users and Groups menu and I would close the menu, then open it again and the group would magically reappear (no popups, errors, or anything). So that puzzled me, after some thought, I realized that it was in use (possibly) so I check the groups of all my users, and like I said, there was a user that had "nx" as its group. So what I did was just change that user to a different group, remove the group and alas! it worked. I was able to install it.
Again,
Thanks to you all.

---

### Post by Brunellus on 2007-01-31
I love it when I get to do this:

THREAD MARKED "SOLVED"

---

### Post by marko_4454 on 2007-03-22
I love that too :)

---

