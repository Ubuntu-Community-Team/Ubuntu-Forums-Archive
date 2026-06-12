---
title: "Apache2 Problem = External Connection Time out"
date: 2008-05-25
forum: General Help
---

### Post by imcensored1 on 2008-05-25
I'm running Hardy and installed Apache2.

I can access my test site from any computer locally (whether i use the static network IP or my IP address assigned by Cox Communications.)  

However no one else on the internet can access it, as they get "Connection Timed out" errors.

my test site is located at: [http://z.speedlinemotorsports.org/](http://z.speedlinemotorsports.org/)

The port forwards are correct, and the router is not blocking connections as people have connected to the FTP server, and both the HTTP site and the SSL site are inaccessible to the interweb.

i am also running firestarter and all ports are allowed through the firewall.

could this be a problem with either apache2.conf or the virtual host conf (for both the port 80 site and the port 443 site)???

thanks
-Kyle

---

### Post by imcensored1 on 2008-05-25
i figured out my problem.

in the virtual host config for both the http and the https sites i had

> ServerName z.speedlinemotorsports.org

the http site became

> ServerName z.speedlinemotorsports.org:80

and the https site became

> ServerName [https://z.speedlinemotorsports.org:443](https://z.speedlinemotorsports.org:443)

-------------

in /etc/apache2/conf.d/fqdn

i had

> ServerName localhost

it is now

> ServerName XX.XX.XX.XX (The server's IP Address
ServerName localhost

--------------

This solved all of my problems except for port 80, which i have determined that my ISP "Cox Communications" has blocked.  I set Apache to run on port 81 and it is working fine... so Cox WILL be getting a phone call on tuesday.

---

