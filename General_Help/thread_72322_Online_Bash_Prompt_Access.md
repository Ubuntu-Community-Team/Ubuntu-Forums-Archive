---
title: "Online Bash Prompt Access"
date: 2005-10-05
forum: General Help
---

### Post by andrewsawyer on 2005-10-05
Hi everyone,
This isn't really an Ubuntu question as such, however...
I have Hoary at home, and I'm on Win2k at work behind a firewall.  I would like to acces my home system every now and again, however I've been told a definate 'no' when I asked about getting PuTTY allowed through the firewall.  I tried anyway, but I've had no luck.
Do any of you know of a way of setting something up on a remote server, or even on my home computer, behind some sort of security, that would allow me to access it?
I'm not 100% sure how this might be done, but I'm thinking something along the lines of an AJAX version of PuTTY, hosted behind a password on a server somewhere.  I have Internet access through the server through IE, giving a username and password.
Does anyone know anyway of doing this, or if there is something already available?  Also, what are the security implications of this?  I guess a hacker could use it to log into a server, and to the server it would be the hosting site that was logging in, but if there was decent security on the hosting site, this shouldn't be a problem would it?
I would appreciate if you could have a think about this and let me know.
Cheers,
Andy

---

### Post by fabiand on 2005-10-06
Hey,

when you know of ajax, you will be able to use google to find teh apropriate tools ... i can tell  you that there _are_ some web based console terminals ... 

- fabiand

---

### Post by andrewsawyer on 2005-10-06
You wouldn't be able to direct me to some sites would you?

Also, there are obvious security issues when logging into your computer from a web based terminal (for starters typing in your IP address, username and password).  Are there any pre-made scripts or something similar that I could upload to my own server?

---

### Post by fabiand on 2005-10-06
Hey,
true - there are huge security issues .. :)
well - you can still use https with a self signed certificat ...
oh: you only _have_ to use a webbase solution when you _have_ to use a roxy ... if your firewall allows outbound connections on port 80 .. just run your ssh server on port 80 ...

oh .. [http://sourceforge.net/projects/phpterm](http://sourceforge.net/projects/phpterm)

- fabiand

---

### Post by andrewsawyer on 2005-10-07
Thank you for the link.

I'll check it out and see how it goes.  Unfortunately, it's not just that the firewall only allows port 80 or 8080, but also that it only allows specific programs to access the Internet.

Fingers crossed I'll be able to get this all up and running.

Thanks again for the info.

Andy

---

