---
title: "Apache2 startup problem."
date: 2005-08-03
forum: General Help
---

### Post by Asm_Freak on 2005-08-03
I just installed apache2 with this command:
sudo apt-get install apache2

I then started apache2 with this command:
sudo /etc/init.d/apache2 start

Everything was successful.  However when I navigate to "http://localhost" I get a connection refused.  If search for an apache process in "ps -aux", there isn't one running.

I then ran "sudo apache2 -E /tmp/aperrors" and in the file /tmp/aperrors I see this
"(13)Permission denied: make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
"
Is there a configuration issue?  I ran "apache2ctl configtest" and that came up ok.

Any ideas on what the problem is?

---

### Post by MoreBikesFewerCars on 2005-08-03
Do you have global read permissions set for your web content directory? Make sure user, group and other all have the read bit set. The directory defaulted to /var/www on my Ubuntu installation.

---

