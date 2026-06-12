---
title: "Access to subdirectory from file"
date: 2013-11-26
forum: General Help
---

### Post by 700 on 2013-11-26
I have new Ubuntu 12.04 LTS. 
Is there any change in Ubuntu or new apache that doesn't allow other files to access subdirectories? 
I haven't change anything, but my php code stopped working on new Ubuntu.

          Example:
The file *test.php*:
**./foo/test.php [-rwxr-xr-x user1]**

doesn't have an access to the *bar* subdirectory (in the same directory):
**./foo/bar/ [drwxr-xr-x user1]**

until permissions are changed to:
**./foo/bar/ [drwxrwxrwx user1]**

  How to get access to the *bar* directory from the *test.php* file without changing permissions?

---

### Post by 700 on 2013-11-28
SOLUTION (not verified) for Ubuntu 12.04 LTS and Apache 2.2.22:
Change Apache ownership

1. Stop *Apache*:
[SIZE=2][COLOR=#696969]*[FONT=courier new]~$ sudo /usr/sbin/apache2ctl stop[/FONT]*[/COLOR][/SIZE]

2. Go to the *etc/apache2* directory:
[SIZE=2][COLOR=#696969][FONT=courier new]*/$ cd etc/apache2*[/FONT][/COLOR][/SIZE]

3. Edit *envvars* file from the *etc/apache2* directory in *gedit*:
[SIZE=2][COLOR=#696969]*[FONT=courier new]~$ sudo gedit envvars[/FONT]*[/COLOR][/SIZE]

4. Change lines *16* and *17*:
[I][SIZE=3][FONT=courier new][COLOR=#000000][SIZE=2]16|[/SIZE][/COLOR][COLOR=#696969][SIZE=2]export APACHE_RUN_USER=_your user name_
[/SIZE][/COLOR][COLOR=#000000][SIZE=2]17|[/SIZE][/COLOR][COLOR=#696969][SIZE=2]export APACHE_RUN_GROUP[/SIZE][/COLOR][COLOR=#696969][SIZE=2]=[/SIZE][/COLOR]*[SIZE=3][FONT=courier new][COLOR=#696969][SIZE=2]_your user name_[/SIZE][/COLOR][/FONT][/SIZE]*[/FONT][/SIZE][/I]

5. Remove */var/lock/apache2* directory:
[COLOR=#696969][SIZE=2][FONT=courier new]*~$ sudo rm -rf /var/lock/apache2*[/FONT][/SIZE][/COLOR]

6. Start *Apache*:
[COLOR=#696969][SIZE=2][FONT=courier new]*~$ sudo /usr/sbin/apache2ctl start*[/FONT][/SIZE][/COLOR]

Could anyone verify this solution, please?

---

