---
title: "Ubuntu 14.04 and sftp problems"
date: 2014-09-23
forum: General Help
---

### Post by dan138 on 2014-09-23
I have an account at Digital Ocean mostly for learning more about system admin (it's a great place to learn IMO).  Anyhow, I set up Ubuntu 14.04, installed the normal LAMP stack. Installed phpmyadmin....  However, when I connect to sftp with my client (I've tried FileZilla and Transport on a mac) I cannot create new folders.  Any help most appreciated.

---

### Post by TheFu on 2014-09-23
Do you understand file and directory permissions?
BTW, why not use "sftp" the client?

Skim the first 200 pgs of this free, pdf book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  There is a section there for permissions.

What are the current permissions, owner, group, and parent directory owner, group and perms?

---

### Post by dan138 on 2014-09-24
> **TheFu said:**
> Do you understand file and directory permissions?


Sort of. I tried setting everything to 777 but that didn't do any good. From mucking around I think I need to do something with user www-data, but I'm not sure what.   /var/www/ is owned by root.  I am logging in as "dan".> 
BTW, why not use "sftp" the client?
Just personal preference.

> 
What are the current permissions, owner, group, and parent directory owner, group and perms?
This is where I get a little confused.

dan@domain:~$ ls -l /var/www
total 4
drwxr-xr-x 2 root root 4096 Aug 26 20:28 html
dan@domain:~$ ls -l /var/www/html/
total 8
-rw-r--r-- 1 root root  1 Sep 22 19:56 index.html
-rw-r--r-- 1 root root 20 Aug 26 20:28 info.php

---

### Post by dan138 on 2014-09-24
Actually, I didn't change anything to 777. I can only do that with sudo.

---

### Post by dan138 on 2014-09-24
This worked:



dan@mojofrog:~$ sudo chown -R dan:www-data /var/www/html
dan@mojofrog:~$ sudo chmod -R g+s /var/www/html

Thanks!

---

### Post by Lars Noodén on 2014-09-24
Actually, you could do it with the group 'dan' also.

```

sudo chown -R dan:dan /var/www/html

```

That would get www-data out of the way since the web server can already read the files.  If the permissions are otherwise as you have shown above.

---

