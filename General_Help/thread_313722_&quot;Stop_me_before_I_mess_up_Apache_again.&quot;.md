---
title: "&quot;Stop me before I mess up Apache again.&quot;"
date: 2006-12-06
forum: General Help
---

### Post by bdmp on 2006-12-06
I just installed apache and I was messing around because I didn't know where to put new web pages I made and I changed apache's "apache2-default" file name. 
After I did that when I accessed [http://localhost/](http://localhost/) I got a "access forbidden" error so I changed it back to "apache2-default"  but I still get the same error. 

Did I change the directory permissions when I changed the name? How can I fix it?

And in related areas...

How do I access the Apache documentation that I installed with synaptic?

and

Where do I find drupal that I installed with synaptic?

forgive me for my ignorance. Thanks :)

---

### Post by mthakur2006 on 2006-12-06
Have you heard of xampp? [www.xampp.org](www.xampp.org) ??

---

### Post by bdmp on 2006-12-06
> **mthakur2006 said:**
> Have you heard of xampp? [www.xampp.org](www.xampp.org) ??

Thank you for the info. I would like to work with what I have now for the time being so, I am still looking for anwsers to those questions.

---

### Post by Wim Sturkenboom on 2006-12-07
You need to restart apache after changes to the config files. And you can check apaches error logs. Not sure where they are in Ubuntu (I use a slackware server), but try */var/log/apache*.

---

### Post by gregor171 on 2006-12-07
Pages you put in /var/www/
what u then see in: [http://localhost/](http://localhost/) 

if you have more virtual directories, u need to set alias:

Restart or "sometines" just reload Apache:
sudo /etc/init.d/apache2 {reload | restart}

This links might help u:
[http://wiki.apache.org/httpd/Info/DistrosDefaultLayout]("http://wiki.apache.org/httpd/Info/DistrosDefaultLayout")
[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html")

---

### Post by gregor171 on 2006-12-07
default u don't mess with. put it back or reinstall. the file yust tell apachi configurations for main web pages... ftm

---

