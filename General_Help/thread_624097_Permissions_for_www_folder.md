---
title: "Permissions for www folder"
date: 2007-11-26
forum: General Help
---

### Post by warby1212 on 2007-11-26
Permissions drive me nutty! 
I'm working in Bluefish html editor. I have a file which is in /var/www/ with permissions:

-rwxrwxr-x  1 schattyste schattyste 12998 2007-11-27 07:30 index.html

When I open this html file in the editor it won't save my changes. 
It saved the changes the first time I saved it but it looks like the first change changed the owner or something and now it won't save anything!

I've exhausted my knowledge of chmod etc (which isn't a lot) Any help appreciated.

---

### Post by 11hjpphty76lkjj on 2007-11-26
Everything looks okay..just for the heck of it:

```
chmod 777 /var/www
```

still not work?

course you really don't want your www directory 777...so this is only a troubleshooting step.

---

### Post by fragos on 2007-11-27
Perhaps the files have a different owner.  My /var/www is root, root bur the folders I've placed in there are user, user.

---

### Post by indytim on 2007-11-27
At the terminal use the 
chgrp
chown 

commands  to change ownership of /var/www to your user (login) id (see the man pages for protocol specifics).

All will be happy after that.

IndyTim

---

### Post by warby1212 on 2007-11-27
Thank you all very much :), I've chgrp and chown successfully. If anyone is still there, looking a the top file which I've just ftp'd down it has different premissions, is that ok or more to the point how does it happen or how can I control that ? 

-rw-r--r-- 1 schattyste schattyste  8522 2007-11-28 07:26 index.php
drwxr-xr-x 6 schattyste schattyste  4096 2007-11-28 06:38 bunna
-rwxrwxr-x 1 schattyste schattyste  3165 2007-11-23 07:58 add.php
-rwxrwxr-x 1 schattyste schattyste  2343 2007-11-23 07:58 add.php.backup
-rwxrwxr-x 1 schattyste schattyste  4950 2007-11-23 07:58 add.php.backupste

---

