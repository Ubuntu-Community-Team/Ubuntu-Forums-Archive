---
title: "What am I missing here? Apache question"
date: 2008-04-16
forum: General Help
---

### Post by bscott3125 on 2008-04-16
I manually installed the latest stable of Apache. It was installed to /usr/local/apache

Now I would like to get it to start on boot, so I did the following after reading some posts here on the forums and elsewhere.

While in the /etc/init.d directory:
sudo ln -s /usr/local/apache/bin/httpd httpd
sudo chmod +744 httpd

I can run sudo ./httpd manually and Apache starts fine. But it does not start on boot.

What am I missing here? :)

Thanks!

---

### Post by tommyhakinen on 2008-04-16
go to System > Administration > Services. Scroll all the way down, you should see Web server (apache2). Check the checkbox then restart. Apache2 should start on startup.
I did the opposite way to stop apache2 to run on startup.
Hope this can help.

---

### Post by juan@forum on 2008-04-16
you need to get or create an initialization script for apache and place it in the /etc/init.d directory

you can't link the daemon httpd service....

---

### Post by bscott3125 on 2008-04-17
> **tommyhakinen said:**
> go to System > Administration > Services. Scroll all the way down, you should see Web server (apache2). Check the checkbox then restart. Apache2 should start on startup.
I did the opposite way to stop apache2 to run on startup.
Hope this can help.

This is already checked with no success

---

### Post by bscott3125 on 2008-04-17
> **juan@forum said:**
> you need to get or create an initialization script for apache and place it in the /etc/init.d directory

you can't link the daemon httpd service....

Ah, ok, that makes sense. Would you happen to have an example of said script?

---

### Post by bscott3125 on 2008-04-18
* bump *

---

