---
title: "Setting up mail/smtp server for web dev testing"
date: 2007-02-06
forum: General Help
---

### Post by OOzypal on 2007-02-06
I do web development and sometime I need to test some functionality of sending email after filling a form. How can I setup my Linux to so I can send email using the php function mail or even use the command line to send emails?

My ISP does not provide me with SMTP access but my web host does. 

Thank you.

---

### Post by Gibbs on 2007-02-06
You want to test locally? First of all you will need a web server, PHP and an SMTP server. On Windows I used a package called [xammp]("http://www.apachefriends.org/en/xampp.html") which nice and easily installs PHP, MySQL and Apache. I've downloaded it for ubuntu too (theres a linux version) but haven't played around with it yet.

You would have to start with getting PHP and a web server running on your desktop first. 

Theres a discussion about different SMTP servers on Ubuntu here:
[http://www.ubuntuforums.org/showthread.php?t=56718](http://www.ubuntuforums.org/showthread.php?t=56718)

Sorry if that isn't very helpful.

---

