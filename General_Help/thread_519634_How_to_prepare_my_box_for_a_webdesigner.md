---
title: "How to prepare my box for a webdesigner"
date: 2007-08-07
forum: General Help
---

### Post by jrattner on 2007-08-07
Currently I have an Ubuntu Lamp setup, and next week I will be having a web designer come in to start designing our corporate website.  I want the designer to have access to Apache Docroot (/var/www), the cgi-bin (/usr/lib/cgi-bin) as well as MySQL and PHP features.  Basically I want the developer to have access to EVERYTHING that they need to develop our website.

What do I need to do and how do I do it?

-Justin

---

### Post by bernied on 2007-08-07
This would depend on the web designer - have they worked with linux before? What do they need? I would do something like this to get started though. 

- look for a group name (System - Users and Groups, or 'sudo cat /etc/groups | grep www' in a terminal) that's been set up specifically for web stuff - I think the group www-data might be setup by default. If you can't find one, add it.
- add a new user and make his primary group the one you found or set up
- navigate to the /var/www folder and set its group ownership ('sudo chown :www-data /var/www'). Do the same for /usr/lib/cgi-bin.
- also make sure it's writeable at the group level ('sudo chmod g+w /var/www')

- optionally, change group ownership of /etc/apache2 and all its contents, though this is probably unnecessary. You probably only need to enable cgi, ssl etc and set up a few subdirectories within /var/www that he/she can work in. It depends on how much you know and they know about configuring apache.

- same goes for mysql, you can either create a user with lots of privileges, for the designer to use, or configure it yourself. You will need to discuss this with them.

- if there is stuff on the box that you don't want the designer to find or see, change the permissions accordingly ('chmod -R o-rwx path/to/private/files'). Most files are readable by 'others', meaning users who don't own the file and are not a member of the group owner of the file, if you see what I mean. Somewhere there is a way of setting the default permissions.

Well, that's something to think about anyway. I hope it is helpful.

---

### Post by jrattner on 2007-08-07
Thanks alot, its a great start.

---

