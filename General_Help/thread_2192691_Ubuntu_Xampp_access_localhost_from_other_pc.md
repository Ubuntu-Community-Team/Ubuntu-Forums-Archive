---
title: "Ubuntu Xampp access localhost from other pc"
date: 2013-12-09
forum: General Help
---

### Post by giannhs905 on 2013-12-09
[COLOR=#000000][FONT=Arial]I am trying to access my localhost from another computer using the local IP(192.168...)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The problem is that I get access forbidden. I changed the httpd-xampp-conf and it looks like the following:

[/FONT][/COLOR]
<LocationMatch "^/(?i:(?:xampp|security|licenses|phpmyadmin|webalizer|server-st$
    Order deny,allow
 Allow from all
                Allow from ::1 127.0.0.0/8 \
           fc00::/7 10.0.0.0/8 172.16.0.0/12 192.168.0.0/16 \
          fe80::/10 169.254.0.0/16


    ErrorDocument 403 /error/XAMPP_FORBIDDEN.html.var
[COLOR=#800000]</LocationMatch>

[COLOR=#000000][FONT=Arial]But still no luck...Any ideas..??[/FONT][/COLOR][/COLOR]

---

### Post by Lars Noodén on 2013-12-09
I would recommend backing up a few steps, removing XAMP, and installing Apache2 from the actual Ubuntu repositories.  Using the repository version, you will have all the configuration files in the right places, along with the binaries in the right places, and nothing unusual.  Also, maintenance and security updates will be tracked automatically and installed with trivial effort.  If you use the XAMP method, you will have to do both the tracking and maintenance manually.  Further, you can end up with redundant versions, such as with Perl which comes pre-installed in standard Ubuntu.  

Also, having things in the standard locations will make it easier for people to help since it will be a familiar environment.

---

### Post by Lars Noodén on 2013-12-09
LAMP is easily installed:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

---

### Post by giannhs905 on 2013-12-09
Ok...I understand that....But I have some databases created in phpmyadmin..How can I keep them.?..Furthermore, is there a graphical interface for mysql if I try sudo apt-get install php5 apache2 mysql

---

