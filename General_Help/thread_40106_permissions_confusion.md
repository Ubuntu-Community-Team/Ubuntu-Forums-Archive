---
title: "permissions confusion"
date: 2005-06-07
forum: General Help
---

### Post by crash369 on 2005-06-07
hello all, i have a perms question.

this is the information on a file
```
-rwxrwxr-x  1 root www-data  472 2005-06-07 00:17 x
```
now, if i belong to www-data group, shouldn't i be able to edit the file? for that matter, if i use the same permissions on a directory, shouldn't i be able to write to that dir?

because i can do none of those things (w/o sudo), and i don't get why.

---

### Post by jameswilhelm on 2005-06-07
You can only work as one group at a time, even if you belong to more. If you want to work as (under?) another group, you have to change your group to another group you belong to.

You use the command newgrp for this.

The command 'sg' apparently runs commands - doing for groups what 'sudo' does for users. Have never used this one myself.

Have look at:
[http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialManagingGroups.html)

I only know how to do this from the command line. The 'Run Application' menu item does not have the option. Would be interested to know if there is a graphical interface for this.

I hope this helps. Please let me know how this goes as I'm still learning and might have missed a subtle point somewhere!

---

### Post by adwait on 2005-06-07
[QUOTE=crash369]hello all, i have a perms question.

this is the information on a file
```
-rwxrwxr-x  1 root www-data  472 2005-06-07 00:17 x
```
now, if i belong to www-data group, shouldn't i be able to edit the file? for that matter, if i use the same permissions on a directory, shouldn't i be able to write to that dir?

because i can do none of those things (w/o sudo), and i don't get why.[/QUOTE]
 Not really sure, coz I am pretty much a newbie....but I think in the line that you posted, www-data is the author of the file and root is the owner. You need to execute the command chown (username) (filename). Then you should be able to read/write without sudo.

---

### Post by skoal on 2005-06-08
[QUOTE=crash369]if i belong to www-data group, shouldn't i be able to edit the file? for that matter, if i use the same permissions on a directory, shouldn't i be able to write to that dir?[/QUOTE]

**Yes**. and, **yes**.  More than likely you have added yourself to the "www-data" group and have all the right directory permissions but you haven't logged out and back in for it to take effect.

For example, I will add myself to the "www-data" group to illustrate:
```
skoal@morpheus://~ $ sudo adduser skoal www-data
Password:
Adding user `skoal' to group `www-data'...
Done.
skoal@morpheus://~ $ groups
skoal adm kmem dialout cdrom floppy audio dip video plugdev users lpadmin scanner admin
skoal@morpheus://~ $ groups skoal
skoal : skoal adm kmem dialout cdrom floppy audio dip www-data video plugdev users lpadmin scanner admin
```
* Oops! You notice how "www-data" shows up as a group I belong to in the second "groups" command but not the first.  If you see that discrepancy for any groups, you know you need to relogin for the changes to take effect.  And, when I do relogin:
```
skoal@morpheus://~ $ groups
skoal adm kmem dialout cdrom floppy audio dip www-data video plugdev users lpadmin scanner admin
```
* and no permission problems now.  Just to illustrate:
```
skoal@morpheus:///tmp $ ls -ald testing/
drwxrwx---  2 root www-data 48 2005-06-08 00:21 testing/
skoal@morpheus:///tmp $ ls -al testing/
total 0
drwxrwx---   2 root www-data  48 2005-06-08 00:21 .
drwxrwxrwt  10 root root     384 2005-06-08 00:20 ..
skoal@morpheus:///tmp $ cd testing
skoal@morpheus:///tmp/testing $ touch hello
skoal@morpheus:///tmp/testing $ ls -al
total 0
drwxrwx---   2 root  www-data  72 2005-06-08 00:21 .
drwxrwxrwt  10 root  root     384 2005-06-08 00:20 ..
-rw-r--r--   1 skoal skoal      0 2005-06-08 00:21 hello
```
For any group modifications, you basically need to relogin for each login session those changes are made.

\\//_

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=adwait]Not really sure, coz I am pretty much a newbie....but I think in the line that you posted, www-data is the author of the file and root is the owner. You need to execute the command chown (username) (filename). Then you should be able to read/write without sudo.[/QUOTE]
 No: it shows that file x is owned by user root and group www-data.

---

### Post by crash369 on 2005-06-08
thank you skoal.  re-logging in made everything work :)

---

### Post by skoal on 2005-06-08
yes, sir.  No problem.  It sounded like you knew what you were doing and had experience with before.  I've scratched my chin many a time wondering the same thing you did here.

\\//_

---

