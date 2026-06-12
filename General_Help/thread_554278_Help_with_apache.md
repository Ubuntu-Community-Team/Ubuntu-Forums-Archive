---
title: "Help with apache"
date: 2007-09-18
forum: General Help
---

### Post by viniciuscarvalho on 2007-09-18
Hello there! I'm trying to get a LAMP service on my personal computer. It's been a while since I've worked with apache (over 5 years) and I'm really confused with 2.0 version :(

I tried to install the server + php5 packages. I start the apache server, but when I try to access [http://localhost](http://localhost) i get an 503 message. There's no error at the logs. Also, is it the same old way to deploy a new application? just put it under /var/www/myapp and then [http://localhost/myapp/index.php?](http://localhost/myapp/index.php?)

Best regards

---

### Post by louieb on 2007-09-18
This helped me figure it out [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by jamvegan on 2007-09-18
Hello.  Yes, a lot of the configuration has moved around or changed, but I don't know why you'd be getting a 503.  Good news is, Apache's running. :-?  What packages did you install, and how did you install them (apt-get, Synaptic, compile from source, ...)?  Did you install libapache2-mod-php5?  As far as deploying a new application, yes, it's still the same.

---

