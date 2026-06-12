---
title: "Samba Help!"
date: 2005-04-11
forum: General Help
---

### Post by s0c0 on 2005-04-11
Okay I have samba setup on my Ubuntu box.  I develope my website in a Windows environment though.  I have shared my /var/www directory and changed ownership to my user account.  I can move files to my /home directory, but I **cannot** move files to my apache share (/var/www/).  When I try doing this I get the following error displayed on my Windows box: *"Cannot copy index: Access is denied. The source file is in use."*

Here is what my samba conf file for the apache share looks like:

[I][Homes]
   comment = Home Directories
   browseable = no
   writeable = yes

[Apache]
   comment = Web Server
   path = /var/www
   public = yes
   writable = yes
   browseable = yes
   valid users = chris 
   create mask = 0770
   directory mask = 0770
[/I]

So what am I doing wrong?  I had absolutely no problems with Slackware when I had Samba set the exact same way.  Your help is appreciated!

---

### Post by dabeej on 2005-04-11
Make sure you have the right permissions set for /var/www

chmod 775 /var/www 
(I think that's what you want)

unless

chmod 777 /var/www
(WHICH IS BAD!!!)

Use group permissions instead. Try that and come back.

---

### Post by s0c0 on 2005-04-12
No the permissions were fine to begin with, but I did what you said anyways and this did not fix the problem (yes I even restarted the daemon).

---

