---
title: "Apache landing page but apache isn't even running or installed"
date: 2015-12-08
forum: General Help
---

### Post by Jeffrey_Becker on 2015-12-08
I'm running Ubuntu Server 14.04 on a hyper-v guest, host is windows 10 pro

I had to reinstall nginx because of a mistake I made to the config and when I did so my domain started dropping to apache's 'It Works!' page
the biggest problem I have with that is that apache2* is uninstalled and netstat shows nothing about apache listening on port 80.

---

### Post by Doug S on 2015-12-08
Getting that page doesn't mean that the Apache web server is running. It only means that apache's default index.html page is still there, in the default document root location (either in /var/www or /var/www/html, depending on your version of Ubuntu).

---

### Post by Jeffrey_Becker on 2015-12-08
I had considered that but didn't look. I figured it wouldn't actually be 'served' since there was no 'server' running.
Thanks for the quick reply.

---

### Post by Doug S on 2015-12-08
> **Jeffrey_Becker said:**
> I had considered that but didn't look. I figured it wouldn't actually be 'served' since there was no 'server' running.
Thanks for the quick reply.Oh. When I replied, I had thought the ngnix server was running and that it had delivered the page.

---

### Post by Jeffrey_Becker on 2015-12-08
> **Doug S said:**
> Oh. When I replied, I had thought the ngnix server was running and that it had delivered the page.
You nailed it. Deleted index.htm and the nginx default page took over.

---

