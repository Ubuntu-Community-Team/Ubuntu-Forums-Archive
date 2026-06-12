---
title: "Help! Lost website after upgrade"
date: 2014-05-20
forum: General Help
---

### Post by chriso0258 on 2014-05-20
Hello,

I was running Ubuntu 13.10 and decided to try upgrading to 14.04. After upgrading, now I can't access my website. When I go to its.chat.tenn all I get is a blank page that says Index of with no files showing. I looked and my site files are still present. Also, I cannot access Webmin. I get an Unable to connect message. When I try to access phpmyadmin I get a page not found.

What is happening and how can I get my site and various applications back?

Thanks for your help.

Chris

---

### Post by Bucky Ball on 2014-05-20
*Thread moved to **General Help**.*

Your machine is serving the webpages? Are you being hosted on someone else's server and you can't access your files and pages? If the latter, perhaps it is something at their end. :-k

---

### Post by Ubi_one_2014 on 2014-05-20
is the websterver started?
did you reboot after the upgrade?

---

### Post by chriso0258 on 2014-05-20
Thanks for your reply. I'm not sure if the webserver is running so I ran /etc/init.d/apache2 start. Server said starting web server apache2. I then tried to access my site with the same results (I get a page that says Index of). I tried accessing [http://localhost](http://localhost) and I get "Unable to connect".  

The server rebooted after the upgrade. 

Also, I am running my own server on a private network at work.

Chris

---

### Post by Bucky Ball on 2014-05-20
I see. So your webpages and web pages are not on the 14.04 machine you are not being able to access them online from, but it is on your own network?

Are you able to access them on the LAN side but not the WAN side?

---

### Post by chriso0258 on 2014-05-20
Sorry if I wasn't clear. I am running my own web server on a private network at work. My website is on this server which was running Ubuntu 13.1 but then I upgraded it to 14.04 by using the upgrade button that showed up. After upgrading I can no longer access my website or the applications I was using for the site (Webmin, phpmyadmin, etc). All my site files are still on the server. DNS is still working. The server retained it's IP address. If I put in [http://its.chat.tenn/index.php](http://its.chat.tenn/index.php) I get a page not found message.

It is acting like Ubuntu changed the default directory for a website from /var/www to something else. 

I'm at a loss but I need to get the site up and running.

Thanks for your help.

---

### Post by Bucky Ball on 2014-05-20
> **Ubi_one_2014 said:**
> is the websterver started?
did you reboot after the upgrade?

? Also wondering if you've rebooted after the upgrade, if that's possible.

---

### Post by chriso0258 on 2014-05-20
Yes, the server was rebooted.

---

