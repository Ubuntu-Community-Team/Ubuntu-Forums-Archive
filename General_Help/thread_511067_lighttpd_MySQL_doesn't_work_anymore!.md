---
title: "lighttpd: MySQL doesn't work anymore!"
date: 2007-07-27
forum: General Help
---

### Post by Der Doktor on 2007-07-27
Hi!

I've set up a lighttpd based homeserver with PHP und MySQL! Everthing worked perfectly!
Yesterday, I restarted lighttpd with
```
sudo /etc/init.d/lighttpd restart
```
Since then, MySQL simply doesn't work! :(
I didn't cange anything in the config files...

Please help me!

---

### Post by zanglang on 2007-07-27
What part, and how exactly, did MySQL not work? Were there any error messages from your PHP scripts? Is your MySQL daemon running fine? (Try connecting to it with 'mysql')

You can also check the lighttpd logs in /var/log/lighttpd/ and see if any interesting shows up.

---

### Post by Der Doktor on 2007-07-27
Hi!

> What part, and how exactly, did MySQL not work?
Wordpress (which I installed at my homeserver) sais:
> Your PHP installation appears to be missing the MySQL which is required for WordPress.

> Is your MySQL daemon running fine? (Try connecting to it with 'mysql')
Yes, MySQL is running! (I even restared the daemon.)

The error.log file in /var/log/lighttpd sais only, that I restarted lighttpd some times! :(

---

### Post by zanglang on 2007-07-27
Hmm... not a problem with lighttpd then. You're missing the MySQL bindings for PHP maybe? (package php5-mysql)

---

### Post by Der Doktor on 2007-07-27
The package php5-mysql is installed! :confused:
I reinstalled it, but nothing did change!

---

### Post by zanglang on 2007-07-28
Did you install Wordpress from the repository? Your SQL settings should be in a file called /etc/wordpress/config-localhost.php or similar, try logging in using the credentials there and see if it works. If you downloaded wordpress yourself there should be a specific config file in your directory also.

---

### Post by Der Doktor on 2007-08-01
Hi!

I solved the problem by reinstalling all components! I hope, this will help permanently!

---

