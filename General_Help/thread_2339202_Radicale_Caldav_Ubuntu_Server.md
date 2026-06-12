---
title: "Radicale Caldav Ubuntu Server?"
date: 2016-10-05
forum: General Help
---

### Post by albert41 on 2016-10-05
Hi,
I have been searching a long while finding a good calendar synchronize for users. Currently Im running Ubuntu server 14.04 with postfix, dovecot, squirrelmail. Recently on of the users asked me if there was a way to sync their calendar from their computer(using pop on outlook) to their iphone, then I thought there has to be. I Installed caldav on outlook, but been having issues installing radicale on the server.
 
This is what I got so far:


[LIST=1]
[*]sudo apt-get install radicale 
[/LIST]
 

[LIST=1]
[*]Next I would edit the file to enable by removing the # 
[/LIST]
ENABLE_RADICALE=yes
[LIST=1]
[*]Then edit the config 
[/LIST]
nano /etc/radicale/config     

[LIST=1]
[*]The config is attached 
[*]Then install apache2 utils to create the users 
[/LIST]
sudo apt-get install apache2-utils
[LIST=1]
[*]Create a test user
sudo htpasswd -cs /etc/radicale/users testuser 
[*]Then to make sure if it works 192.168.3.150:5232 
[/LIST]
Then it ask username and password I enter it but get a blank page when I should get a “Radicale works”
So not sure where to turn or what to do?
 
Thank you

---

