---
title: "Apache process killed every 3 seconds, can't log into console. What is happening?"
date: 2013-05-18
forum: General Help
---

### Post by ingramproductions on 2013-05-18
My ubuntu server has been doing this every few days (see attached). The apache process is killed about every 3 seconds and it says out of memory on the console. I can't even log into the console.
What causes this to happen?
It's an Ubuntu 10.04 virtual machine with 3gb of memory and minimal traffic to it. It is also updated.

Any ideas?

[ATTACH=CONFIG]242736[/ATTACH]

---

### Post by 2F4U on 2013-05-19
What are you running on the Apache server? For example Java, PHP, Perl consume a lot of memory. But it may also be another application that eats up all the memory and Apache is just the application that suffers from this.

---

### Post by ingramproductions on 2013-05-19
Php. As I said, I couldn't even log into the console, so I had to do a hard restart. Is there anyway to find out what caused this?

---

### Post by Lars Noodén on 2013-05-19
You could open a console or terminal and monitor memory usage using [top](http://manpages.ubuntu.com/manpages/raring/en/man1/top.1.html)  If you are able to reproduce the problem on demand, then you can see what's using the RAM 

Also, you could open another terminal and monitor the error log for the web server.

```

tail -f /var/log/apache2/error.log

```

---

