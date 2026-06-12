---
title: "proftpd"
date: 2007-02-02
forum: General Help
---

### Post by mymuscle on 2007-02-02
Hey guys, I got my lamp server setup and every thing seems to be smooth.

Im trying to get the proftpd portion of Webmin working, but it wont install properly. In the middle of the installation is says :
E: couldnt find package proftpd 

Im doing this all from the CLI, im not using a GUI, ive learned alot about CLI and i love it! can anyone help me to properly get the proftpd working?

---

### Post by ew16301 on 2007-02-02
I actually JUST started doing the exact same thing on Server edition of Edgy. I believe you need to install proftpd. You can get it at

[http://www.proftpd.org/download.html](http://www.proftpd.org/download.html)

And you can find help with the install here

[http://www.proftpd.org/localsite/Userguide/linked/userguide.html](http://www.proftpd.org/localsite/Userguide/linked/userguide.html)

Otherwise, if you need some more help feel free to PM or email me. Hope this helps

---

### Post by mymuscle on 2007-02-02
thank you so much!!!!

---

### Post by PhineasFreak on 2007-02-05
I'm having the very same problem and I'm also using CLI.

How do I download at the CLI prompt when apt-get fails?

:-(

thanks.

---

### Post by el_rata on 2007-02-15
uncomment the universe/multiuniverse repositories in the /etc/apt/sources.list

---

