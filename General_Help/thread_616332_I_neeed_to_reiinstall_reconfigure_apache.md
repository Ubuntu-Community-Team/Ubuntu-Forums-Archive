---
title: "I neeed to reiinstall reconfigure apache"
date: 2007-11-18
forum: General Help
---

### Post by Jason Weiss on 2007-11-18
Hi

A while back I was foolishly experimenting with all things apache. 

I was very excited about ubuntu and I was trying to install every web package I could get my hands on including ampache.

As a result I seriously stuffed LAMP, so I just left it alone. 

Well anyway now I have matured a little and I have bou8ght a domain and I have installed NOIP and I would like to host my own website. 

Except I forgot, I wrecked apache, So I tried reinstalling apache, but it does not help, because the program is so smart it knows not to reconfigure itself when upgrading. 

I am about to wip my drive and just start again.

 But then I think to myself, the is Ubuntu, it is smarter than that, I should not have to do that. 

I am sure that some on out there can give me a simple way to make apache like new. :guitar:

---

### Post by zvacet on 2007-11-18
```
sudo aptitude remove --purge packagename
```

packagename is of course exact name of apache

---

### Post by Jason Weiss on 2007-11-18
> Firefox can't establish a connection to the server at localhost.

I am sorry i am still having the same problem i have tried purging but I am not have my success

---

### Post by jordanmthomas on 2007-11-18
After removing apache, you will probably want to install it again.  :)

---

### Post by Jason Weiss on 2007-11-18
> **jordanmthomas said:**
> After removing apache, you will probably want to install it again.  :)

I should have specified, I reinstalled.  :)

But when I try to go to local host I still get the same error page.

---

### Post by jordanmthomas on 2007-11-18
Ok, first things first:
1.  Is apache started?
```
ps -A | grep apache
``` or ```
ps -A | grep http
```
one of these should return something.
If not, start it
```
sudo /etc/init.d/apache start
```
(not sure exactly what ubuntu calls apache...could be httpd, or apache2, or something similar)
2.  Is it listening on any ports?
```
netstat -l | grep tcp
```

---

### Post by Jason Weiss on 2007-11-18
Hmm I am not sure what I doing wrong 

When I do this:

> sudo /etc/init.d/apache start

I get this:

> jason@jason-desktop:/usr/local/bin$ sudo /etc/init.d/apache2 start
 * Starting web server (apache2)...                                             Syntax error on line 2 of /etc/apache2/sites-enabled/000-default:
<VirtualHost> directive requires additional arguments
                                                                         [fail]
jason@jason-desktop:/usr/local/bin$ 


---

### Post by Jason Weiss on 2007-11-18
I think I mightjust reinstall the OS. 

It is a shame, I was sure there would be a simpler answare than that.

---

