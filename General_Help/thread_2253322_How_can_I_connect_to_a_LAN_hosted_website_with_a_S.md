---
title: "How can I connect to a LAN hosted website with a Samsung Galaxy S3 phone?"
date: 2014-11-18
forum: General Help
---

### Post by Marcelo Ruiz on 2014-11-18
Hi All,

I have a weird request that is driving me crazy: I want to access a LAN hosted website (in Apache2 running on Ubuntu) through my phone connected to the wifi network.
So far it has been possible for me to:

* Access the Apache Ubuntu Default Page "It works" webpage from my phone using in my phone my computer local IP address (10.0.0.3).
* Access a phpinfo.php file located in /var/www/html using (10.0.0.3/phpinfo.php)
* Access a phpinfo2.php file located in /var/www/html/testdir using (10.0.0.3/testdir/phpinfo2.php)

Now, I cannot access a file called index.php located in /var/www/html/mywebsite from my phone (but I can from any other computer conected to my router).
Each time I try to connect I get: :

```

Error 500
Got the error: Server Error while trying to obtain http://marcelo-computer/mywebsite
Unknown host

```

How is this possible? My 000-default.conf in under sites-available looks like follows:

```

<VirtualHost *:80>

	ServerAdmin webmaster@localhost
	DocumentRoot /var/www/html

	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>

<Directory "/var/www/html">
    AllowOverride All
</Directory>

```

I tried to add "Allow from all" to the Directory section but it changed nothing.
I also tried to create a new Directory section pointing to "/var/www/html/mywebsite" with "Allow from all", but it did not solve the problem.
Does anyone have an idea of what the problem might be?
I don't want to set a port forwarding in my router and use the external IP address to access the website.

Thanks!

---

### Post by TheFu on 2014-11-19
I suspect that the phone doesn't know what marcelo-computer is.  Use the IP address.

Also, check the apache log files in /var/log/apache2/* for errors. This way you can tell when/if the phone is actually getting to the web server or not - plus any errors.

/var/www/mywebsite is not under /var/www/html/ .... put it into /var/www/html/mywebsite and see if it doesn't work.

---

### Post by Marcelo Ruiz on 2014-11-19
@TheFu

Thanks for your answer. I made a mistake when I wrote the post. mywebsite *is* in the /var/www/html folder.
I checked the log files and there are no errors. By looking at access.log I can see the IP of the phone (exactly in the same way I see it when I access the files that I mentioned in my previous post, which are displayed correctly).
The error 500 I posted is as shown on the phone, even though I use marcelo-computer's IP address in browser like this: "http://10.0.0.3/mywebsite".
The weird thing is the error is displayed just for mywebsite...

---

