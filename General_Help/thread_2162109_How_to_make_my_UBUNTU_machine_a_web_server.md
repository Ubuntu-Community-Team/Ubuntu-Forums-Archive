---
title: "How to make my UBUNTU machine a web server"
date: 2013-07-13
forum: General Help
---

### Post by YohannesJ on 2013-07-13
I have installed Ubuntu 12.04 on my virtual machine. I want that machine to be a web server. I have my public IP, enough storage and every thing else; no worries.
What I really need a help on is that, I just installed only the Ubuntu OS and I want to make this machine to be my web server. I some how know the stuffs to be installed but I need an advice on the CORRECT precedence (which one should be installed first and which goes next) and I also like to know how to secure my phpmyadmin out of the root (www) folder either during or after installation. I don want any one to sniff on my DB through  [ mywebsite/phpmyadmin ].
I hope to get the support as soon as possible!!
Thank you so much!!
YohannesJ 
;)

---

### Post by kc1di on 2013-07-13
Hello YohannesJ and welcome to Ubuntu,

[Here is a page]("http://funwithlinux.net/2012/05/ubuntu-12-04-web-server/") that lays it out quite simply it may be of help.

---

### Post by Cheesemill on 2013-07-13
If you want to install the standard LAMP stack (Linux, Apache, MySQL, PHP) then you can do it with the following command...
```
sudo apt-get install lamp-server^
```

If this is going to be a public-facing webserver then I wouldn't install phpmyadmin as it's just another thing that needs securing (I never use it anyway). You will probably only need to create  users and databases when initially setting up your site, this can all be done using the mysql command line tool.

---

### Post by chkneater on 2013-07-13
Might be easiest just ot install the server version of your distro from ubuntu.

---

