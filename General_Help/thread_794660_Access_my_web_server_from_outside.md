---
title: "Access my web server from outside?"
date: 2008-05-14
forum: General Help
---

### Post by Arenlor on 2008-05-14
I have a web server on my computer (Apache) which is a Hardy Heron. I have my router setup to forward all TCP traffic on certain ports to it (818*) and want to know, how do I set it up to accept outside traffic? This is just a thing so that a few people can look at a page or two every so often so it isn't important to have anything special setup just access. I don't even need FTP access.

---

### Post by Monicker on 2008-05-14
Modify /etc/apache2/ports.conf.  Change line which reads "Listen 80" to the port of your choosing.

---

### Post by IanShuttleworth on 2008-05-14
Do what Monicker said, and if you use a port other than 80, you'll probably need to add ":[port]" to the end of whatever hostname of your server is, or the ip address, like
123.123.123.123:99    if the port was 99.

---

### Post by Joeb454 on 2008-05-14
Forward port 80 on your router to the machine that you want to use as the webserver :)

---

