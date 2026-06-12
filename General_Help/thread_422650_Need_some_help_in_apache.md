---
title: "Need some help in apache"
date: 2007-04-25
forum: General Help
---

### Post by linducky on 2007-04-25
Hey you guys just recently switched over to using UBUNTU and i do web page development so i wanted to know if you guys can give me some help on a problem i am experiencing.

i installed apache2 and php5 and mysql and all seems to be working well but when i create my public_html folder in my hone folder and the i go to my browser and type in localhost/~username i get a 404 not found error

i know everything is working otherwise because i have created files in /var/www and accesed them but i cannot understand why i cannot get my public_html working

could this be a permissions error or do i have to edit the apache conf file?

please help me because i am new to linux and do not know....

---

### Post by FluffyElmo on 2007-04-25
You'll have to enable this in your Apache configuration. The following document should help, your httpd.conf file is most likely located in /etc/apache2/httpd.conf or you can add a virtual host in /etc/apache2/sites/enabled/
[http://httpd.apache.org/docs/2.0/howto/public_html.html]("http://httpd.apache.org/docs/2.0/howto/public_html.html")

---

### Post by linducky on 2007-04-25
thanks for the assist man but i decided that i going back to version 6.10 because i was getting some other bugs in 7.04 as well, including a startup disk cheacking error and varios other things didnt feel just right... i think ill just work from this version for the hour...
thanks again though man

---

