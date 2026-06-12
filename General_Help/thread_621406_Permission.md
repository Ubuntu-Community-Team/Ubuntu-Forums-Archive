---
title: "Permission"
date: 2007-11-23
forum: General Help
---

### Post by AllanP on 2007-11-23
Something goofy has happened and I can't for the life of me think of anything I did to cause it. I had auto login enabled and now I have to log in. Also I was configuring access to a partition and when in terminal I typed "ls -la" I got a whole whack of stuff listed. Here is the output of "ls -la"
allan@allan:~$ sudo mount -a
allan@allan:~$ ls -la
total 192
drwxr-xr-x 33 allan allan 4096 2007-11-23 13:32 .
drwxr-xr-x  3 root  root  4096 2007-11-20 11:34 ..
-rw-------  1 allan allan  787 2007-11-22 18:44 .bash_history
-rw-r--r--  1 allan allan  220 2007-11-20 11:34 .bash_logout
-rw-r--r--  1 allan allan 2298 2007-11-20 11:34 .bashrc
drwxr-xr-x  3 allan allan 4096 2007-11-20 19:38 .cache
drwxr-xr-x  4 allan allan 4096 2007-11-20 22:08 .config
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:38 Desktop
-rw-------  1 allan allan   28 2007-11-23 13:32 .dmrc
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:38 Documents
-rw-------  1 allan allan   16 2007-11-20 19:38 .esd_auth
lrwxrwxrwx  1 allan allan   26 2007-11-20 11:34 Examples -> /usr/share/example-content
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:38 .fontconfig
drwx------  4 allan allan 4096 2007-11-23 13:32 .gconf
drwx------  2 allan allan 4096 2007-11-23 13:33 .gconfd
-rw-r-----  1 allan allan    0 2007-11-22 12:50 .gksu.lock
drwxr-xr-x  3 allan allan 4096 2007-11-20 19:38 .gnome
drwx------  8 allan allan 4096 2007-11-23 05:32 .gnome2
drwx------  2 allan allan 4096 2007-11-20 19:38 .gnome2_private
drwxr-xr-x  2 allan allan 4096 2007-11-20 21:15 .gstreamer-0.10
-rw-r--r--  1 allan allan  140 2007-11-23 13:32 .gtk-bookmarks
-rw-r--r--  1 allan allan   87 2007-11-20 19:38 .gtkrc-1.2-gnome2
-rw-------  1 allan allan  157 2007-11-23 13:32 .ICEauthority
drwxr-xr-x  3 allan allan 4096 2007-11-20 22:07 .java
drwxr-xr-x  3 allan allan 4096 2007-11-20 19:38 .local
drwx------  3 allan allan 4096 2007-11-20 22:06 .macromedia
drwx------  3 allan allan 4096 2007-11-20 19:38 .metacity
drwx------  4 allan allan 4096 2007-11-20 22:03 .mozilla
drwx------  3 allan allan 4096 2007-11-20 21:54 .mozilla-thunderbird
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:38 Music
drwxr-xr-x  3 allan allan 4096 2007-11-23 05:32 .nautilus
drwx------  3 allan allan 4096 2007-11-21 06:43 .openoffice.org2
drwxr--r--  2 allan allan 4096 2007-11-20 19:49 .pcmanfm
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:38 Pictures
-rw-r--r--  1 allan allan  566 2007-11-20 11:34 .profile
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:38 Public
-rw-------  1 allan allan  608 2007-11-21 06:42 .recently-used
-rw-r--r--  1 allan allan 1906 2007-11-23 05:32 .recently-used.xbel
-rw-r--r--  1 allan allan    0 2007-11-20 19:38 .sudo_as_admin_successful
drwxr-----  3 allan allan 4096 2007-11-20 22:02 temp
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:38 Templates
drwxr-xr-x  4 allan allan 4096 2007-11-22 15:45 .tomboy
-rw-r--r--  1 allan allan 5432 2007-11-22 16:03 .tomboy.log
drwx------  2 allan allan 4096 2007-11-20 19:38 .Trash
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:50 .update-manager-core
drwx------  2 allan allan 4096 2007-11-20 19:38 .update-notifier
drwxr-xr-x  2 allan allan 4096 2007-11-20 19:38 Videos
drwxr-xr-x  2 allan allan 4096 2007-11-22 16:03 .wapi
-rw-------  1 allan allan  116 2007-11-23 13:32 .Xauthority
-rw-r--r--  1 allan allan 1579 2007-11-23 13:32 .xsession-errors

---

### Post by mali2297 on 2007-11-23
> **AllanP said:**
> Also I was configuring access to a partition and when in terminal I typed "ls -la" I got a whole whack of stuff listed. 

That list seems normal, what is the problem?

---

### Post by nick_h on 2007-11-23
Yes it looks normal.  Try:
```
ls -l
```
if you don't want to list the hdden files that start with a ".".

---

### Post by AllanP on 2007-11-23
> **mali2297 said:**
> That list seems normal, what is the problem?
Well whenever I've done that before all I got was a hand full partitions that were owned by me not every folder under my control.
What started me on this was that I have to log in every time when I had it set to "Enable automatic login" and still is.

---

### Post by AllanP on 2007-11-23
> **nick_h said:**
> Yes it looks normal.  Try:
```
ls -l
```
if you don't want to list the hdden files that start with a ".".

I have no secrets lol; here:

total 32
drwxr-xr-x 2 allan allan 4096 2007-11-20 19:38 Desktop
drwxr-xr-x 2 allan allan 4096 2007-11-20 19:38 Documents
lrwxrwxrwx 1 allan allan   26 2007-11-20 11:34 Examples -> /usr/share/example-content
drwxr-xr-x 2 allan allan 4096 2007-11-20 19:38 Music
drwxr-xr-x 2 allan allan 4096 2007-11-20 19:38 Pictures
drwxr-xr-x 2 allan allan 4096 2007-11-20 19:38 Public
drwxr----- 3 allan allan 4096 2007-11-20 22:02 temp
drwxr-xr-x 2 allan allan 4096 2007-11-20 19:38 Templates
drwxr-xr-x 2 allan allan 4096 2007-11-20 19:38 Videos

---

