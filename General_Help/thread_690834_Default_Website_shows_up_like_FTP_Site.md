---
title: "Default Website shows up like FTP Site???"
date: 2008-02-07
forum: General Help
---

### Post by SierraDump on 2008-02-07
Hello, 

I am wondering why after a default install of Ubuntu 7.10 (gutsy) Server with the LAMP Server selected, when accessing the IP Address of the server a "FTP-looking" directory structure appears and I have to click on "APACHE2-Default" before the "test/home page shows up".

The reason I ask is because I am following this tutorial:  [http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated)

and am installing BASE (basic analysis and security engine) and when the install is done - I get 2 directories when accessing the IP Address of the server (APACHE2-Default and BASE).

This is somewhat annoying as I was hoping it would just drop me into the BASE directory?

Is this normal behavior for a LAMP install???  I seem to remember on my CentOS server and LAMP install that typing the IP Address of the server brought me to the apache "TEST/HOME PAGE"....

THANK YOU!

---

### Post by bilge.tutak on 2008-02-07
I think that is normal behavior unless you define a primary index page.

---

### Post by SierraDump on 2008-02-08
So you are saying that by default, a user/guest trying to access a website that is located on the server, must first click on the apache folder?

---

### Post by jd65pl on 2008-02-09
This is normal you do not have an index.xxx page in the folder /var/www/

---

### Post by bilge.tutak on 2008-02-19
Yeap you should have a default web page (index.php, index.html ...) for a web page to come up.

---

