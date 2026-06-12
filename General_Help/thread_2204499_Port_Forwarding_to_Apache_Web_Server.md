---
title: "Port Forwarding to Apache Web Server"
date: 2014-02-08
forum: General Help
---

### Post by jay30 on 2014-02-08
I have setup Ubuntu 12.04 Server and installed an Apache2 web server.  I have also installed Wordpress (and setup a basic web page).  I can access my web page from an internal PC (ie. via my home wireless).  I have an Actiontec V1000 modem/router from Telus (my ISP).  I have setup port forwarding on my router in order to allow ssh access to the server.  In particular I have forwarded port 22 to the IP address of my server.  This works ok (I can access via an internal PC or an external one using the modem IP address).

i am now trying to setup port forwarding such that I can get to my web page from an external PC. As I understand that Telus blocks port 80, I have port forwarded port 8080 on my modem to the IP address of my server.  I have also made the following changes/additions to my /etc/apache2/ports.conf and /etc/apache2/sites-available/default files:

PORTS.CONF
NameVirtualHost *:80  [this line was already here]
Listen 80  [this line was already here]
Listen 8080  [I added this line]

DEFAULT
Replaced first line of file "<VirtualHost *:80>" with "<VirtualHost *:8080>"

I then restarted Apache2.

Now, when I try to browse to my web page from an external PC via http://<modem IP>:8080 I receive the following message on my browser:

NOT FOUND
The requested URL / was not found on this server.
Apache/2.2.22 (Ubuntu) Server at 123.4.567.891 Port 8080

Any idea what I am missing?  It seems encouraging that it is maybe finding the server?  Are there maybe additional/different entries to be made in other Apache configuration files?  Should I have somehow kept both VirtualHost lines in the default file?

Any suggestions/ideas greatly appreciated.  Thank you.

---

### Post by SeijiSensei on 2014-02-08
It would be easier if you forward port 8080 back to port 80 on the server.  There's no requirement that the same port be used in both places.  Some brain-dead routers impose the same-port requirement though.

---

### Post by jay30 on 2014-02-09
My modem/router seems to maybe allow this (at least I have set up what I believe to do that), however, hasn't helped.  In fact, the external browser then seems to not get as far as it does otherwise (ie. doesn't indicate anything about knowing it is a ubuntu server),

---

### Post by jay30 on 2014-02-13
Any other ideas / suggestions for this problem?

---

