---
title: "PHP exec() permissions"
date: 2007-09-18
forum: General Help
---

### Post by skunkwerk on 2007-09-18
Hi,
   I have a C program located in /var/www/ which needs to write out a file to a folder in /var/www/

I'd like to call this program from PHP using th exec or system commands
however, when I do so the program responds with an error saying it wasn't
able to write the file.

when i do this via the command-line it works fine.  I have checked that safe-mode is off in PHP, and 'whoami' reports that apache/PHP is running as user "www-data"

I have added this to my /etc/sudoers - prototype is the name of the c program:
www-data ALL=NOPASSWD:/var/www/prototype

when I issue this command in php, it still does not work though:
system("sudo /var/www/prototype \"/var/www/pending/file1.txt\" ");

i've set the permissions to the prototype c program to 777 with user & group www-data

any ideas?

thanks

---

### Post by kebes on 2007-09-18
The problem may occur when the webserver tries to write the file. If the user "www-data" is trying to write the file "/var/www/pending/file1.txt", it may not have the correct permission to do so. You can of course make the file/directory writeable by everyone:
```

cd /var/www/
sudo chmod 777 pending
cd pending
chmod 777 file1.txt

```

Alternately, you can change ownership:
```

cd /var/www/
sudo chown www-data:www-data pending
cd pending
sudo chown www-data:www-data file1.txt

```


(Note: You may not need to add "www-data" to the sudoers file. In most cases you can just set ownership/permissions that the webserver needs.)

---

### Post by skunkwerk on 2007-09-19
nope, that didn't work.  and i've already added www-data to my sudoers file.

---

