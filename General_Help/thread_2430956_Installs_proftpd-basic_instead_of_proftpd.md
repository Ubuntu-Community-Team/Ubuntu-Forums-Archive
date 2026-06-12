---
title: "Installs proftpd-basic instead of proftpd"
date: 2019-11-09
forum: General Help
---

### Post by jasper1378 on 2019-11-09
Hello all,

I'm setting up an old desktop as server for fun. I'm trying to set up FTP. When I run "sudo apt-get install proftpd" it automatically installs proftpd-basic, how do I stop it from doing this so I can just install proftpd? I'm on Ubuntu 18.04.

---

### Post by uRock on 2019-11-09
Hello and welcome,

That package "proftpd" does not exist. [https://packages.ubuntu.com/search?keywords=proftpd](https://packages.ubuntu.com/search?keywords=proftpd)

---

### Post by jasper1378 on 2019-11-09
Then what package would I use? I need it to work with gadmin-proftpd. Here is the article that I am following. [https://www.instructables.com/id/Set-up-your-very-own-Web-server/](https://www.instructables.com/id/Set-up-your-very-own-Web-server/)

---

### Post by dragonfly41 on 2019-11-09
The tutorial you refer to is very dated.

You could experiment with [ngrok]("https://ngrok.com/") and setup PuTTY SSH sessions instead of FTP.

---

### Post by uRock on 2019-11-09
> **jasper1378 said:**
> Then what package would I use? I need it to work with gadmin-proftpd. Here is the article that I am following. [https://www.instructables.com/id/Set-up-your-very-own-Web-server/](https://www.instructables.com/id/Set-up-your-very-own-Web-server/)

Install the **gadmin-proftpd** package and it will bring in all of its dependencies.

Looking at the screenshot for step 3 tells me it is almost ten years old and likely to not match up with today's packaging.

I would recommend following this tutorial. [https://help.ubuntu.com/lts/serverguide/ftp-server.html](https://help.ubuntu.com/lts/serverguide/ftp-server.html)

---

