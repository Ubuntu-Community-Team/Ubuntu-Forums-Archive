---
title: "access denied"
date: 2008-06-22
forum: General Help
---

### Post by alantony on 2008-06-22
Ubuntu 7 server
windows development environment phpEd


Hi, 
We(my team) are new to ubuntu but love it so far.    my question is long winded....I am working in a development environment (phpEd) on windows with a large project hundreds of files on an Ubuntu server.  I can access my home directory ubuntu/home/me with filezilla and my IDE.  I have used putty to move files from my directory to the /var/www folder.  My question is how can I gain access to the /var/www folder from my IDE.  I can see the file structure of the /var/www folder and download the files in that folder (/var/www) but I need to modify the files in the /var/www folder.  Please help it is simply not practical to move each modified file from my home directory to the /var/www folder.  Is it possible to login as root with filezilla or my phped IDE.  or create an account with root privileges for that folder.    thanks in advance.
al
"What good is security if it makes you a prisoner."

---

### Post by fahadsadah on 2008-06-22
You could of course log in as root. You just need to give root a password: ```
sudo passwd
```.
You could also set an account's UID to 0, but this is less secure.

It is also possible to give everyone write access to /var/www: ```
sudo chmod 777 /var/www
```
Want to restrict this to a single group? ```
sudo chmod 774 /var/www && sudo chgrp the_group_who_should_have_write_access /var/www
```

---

### Post by alantony on 2008-06-22
Hey thanks for your reply.
 
I setup a password for root and I was able to login via putty as root@ubuntu:

Also, I changed the permissions for the /var/www folder to 777.  However, I still cannot access the /var/www folder via filzilla or my php IDE.  

To begin with, I cannot login as root via filezilla or the IDE. 

is there a restriction to remote access as root.
I'm stumped...
any other suggestions.
much thanks
al

---

### Post by ddales on 2008-06-22
root logins via ftp are disabled by default.

Depending on what ftp service you're using you'll have to change the configuration in order to allow root access.

---

### Post by alantony on 2008-06-22
change what?

the ftp service configuration

or 

the ubuntu configuration

thanks

---

