---
title: "Can I use my system as a web page hoster?"
date: 2007-08-01
forum: General Help
---

### Post by rubperezt on 2007-08-01
Can  i use my system as a web server to host my own web page while my pc is online? if so how?

---

### Post by splintercellguy on 2007-08-01
Sure. You'll need to install and configure the Apache web server. As for how, I honestly have no idea, though there are probably guides to do this.

---

### Post by Malh on 2007-08-01
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

I believe that's what you're looking for.

---

### Post by aysiu on 2007-08-01
Once you have Apache installed, you can put files in the /var/www directory (you'll need root privileges to do this, so you should *sudo cp* the files there). When you launch your web browser, type ```
http://localhost
``` in the location bar to see your web page.

---

### Post by Malh on 2007-08-01
And if you want to view it over the internet, you would need a static IP, and you could register a domain name, or just access it through the static IP.

---

### Post by rubperezt on 2007-08-01
the static ip is necesary or just recomended? like.... if i have a dynamic one i could acces to my pc eventhou tomorrow i'll have to access thru another ip?

---

