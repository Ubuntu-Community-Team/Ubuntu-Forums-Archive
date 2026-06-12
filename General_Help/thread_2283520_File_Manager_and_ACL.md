---
title: "File Manager and ACL"
date: 2015-06-22
forum: General Help
---

### Post by asusv2 on 2015-06-22
Can the file manager in ubuntu be configured to work with folders that have default ACL permissions assigned? 


This is my problem: I have a folder with default acl permissions. When files are created in that folder they all get this permissions assigned to them.
When the files are created outside of that folder and are later moved or copied in that folder, using the terminal commands 'cp' or 'mv' works like it should, but when i try to move the files with the file manager (drag & drop) the permissions stay the same as they were outside of the folder.


Any idea? Thank you

---

### Post by deadflowr on 2015-06-22
Not sure it helps but there is a package the will allow working with acls in the default file manager nautilus
It's called eiciel.
It's in the Ubuntu software repositories.

reference on acls in Ubuntu:
[https://help.ubuntu.com/community/FilePermissionsACLs](https://help.ubuntu.com/community/FilePermissionsACLs)

reference on eiciel
[http://rofi.roger-ferrer.org/eiciel/](http://rofi.roger-ferrer.org/eiciel/)

To install a simple
```
[sudo apt-get install eiciel
```
should do it.

Like I stated, do not know if it'll help, but I hope it does.

---

### Post by asusv2 on 2015-06-22
Thank you, just tried eiciel, it is a graphical interface for assigning acl's to folders and does not change the way the file manager works with them.

---

### Post by jamesisin on 2015-06-22
Is this a local or remote directory?

---

### Post by deadflowr on 2015-06-22
> **asusv2 said:**
> Thank you, just tried eiciel, it is a graphical interface for assigning acl's to folders and does not change the way the file manager works with them.
It integrates with nautilus, the default file manager.
You need to kill the existing nautilus session, which keeps running on Ubuntu, because it handles the desktop.
Run:
```
nautilus -q
```
if -q fails to kill/stop nautilus, try it with --quit.
When you restart the file manager it'll show the eiciel options.

---

### Post by asusv2 on 2015-06-22
> **jamesisin said:**
> Is this a local or remote directory?

it is local, on the same partition as the system

---

### Post by asusv2 on 2015-06-22
> **deadflowr said:**
> It integrates with nautilus, the default file manager.
You need to kill the existing nautilus session, which keeps running on Ubuntu, because it handles the desktop.
Run:
```
nautilus -q
```
if -q fails to kill/stop nautilus, try it with --quit.
When you restart the file manager it'll show the eiciel options.

For me this is not working, stopping nautilus did nothing. Started eiciel with root privileges, made the permissions with it(which is a little buggy) and still no change.
Think I just have to live with this and create files only in that folder and use the terminal for copying.

Thank you all anyway.

---

