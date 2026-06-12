---
title: "www-data user for web development"
date: 2014-03-18
forum: General Help
---

### Post by alain.roger on 2014-03-18
Hi,

i installed under VirtualBox a ubuntu 13.10 desktop version, so i can test some applications and also develop websites.
when i use my windows computer and eclipse to connect to ubuntu web server i use eclipse.
when eclipse create a file in webserver directory, i can see user:group = www-data:www-data

i understood the www-data is apache2 user:group by default.
Q1. is it correct ?

this avoid my default ubuntu user to change those files...
therefore i have 2 choices:

1. to add my default ubuntu user to www-data group
2. to change apache2 default user:group to my default ubuntu user.

Q2: what is the best solution ?

thx a lot.

Al.

---

### Post by Lars Noodén on 2014-03-18
Actually the correct response is neither.  The user www-data exists for privilege separation, to provide an unprivileged user for the web server to run as.  It should ideally not have write access anywhere pages are served via https or http.  If you want write access to the /var/www directory and you the are only user, you can take ownership of it with chown.  If you are going to share write access with others, then groups are the way to go instead.  Either way, the directories shoud definitely not be owned by www-data.

---

### Post by alain.roger on 2014-03-19
thx Lars,

but how can i do when we (my friend and i) use Eclipse to create files and that Eclipse created file got automatically owner "www-data:www-data" ? i don't understand how is it possible as for example, i use my ubuntu default account to connect via ssh, to web server... i don't know where this www-data comes from :(

---

### Post by mastablasta on 2014-03-19
but default ubuntu user is higher than www-data so the user it self should have write permissions on those files. whereas "user" www-data will have read only permission on the files (which is correct).

i am not sure what you want to do. do you want that you and your friend can access and edit the file you create in eclipse?

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

> [h=2]Using Apache[/h]
You can access apache by typing 127.0.0.1 or [http://localhost]("http://localhost/") (by default it will be listening on port 80) in your browser address bar. By default the directory for apache server pages is /var/www . It needs root access in order to put files in. A way to do it is just starting the file browser as root in a terminal: $ gksudo nautilus
or 
if you want to make /var/www your own. (Use only for non-production web servers - this is not the most secure way to do things.) $ sudo chown -R $USER:$USER /var/www

---

### Post by Lars Noodén on 2014-03-19
What method are you using to transfer the files from where you are working on them over to the server?  And once on the server what are the permissions on that directory?  If it is /var/www, then

```

ls -lh /var/www

```

---

