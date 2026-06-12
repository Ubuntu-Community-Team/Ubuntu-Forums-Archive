---
title: "Nginx and phpmyadmin"
date: 2017-12-12
forum: General Help
---

### Post by ELMIT on 2017-12-12
I got nginx setup and switched to https.

I have several config files for each subdomain.
```

server {
	listen 80;
	listen [::]:80;

	root /home/tools.site.com;

	# Add index.php to the list if you are using PHP
	index index.php index.html index.htm index.nginx-debian.html;

	server_name tools.site.com;

	location / {
		# First attempt to serve request as file, then
		# as directory, then fall back to displaying a 404.
		try_files $uri $uri/ =404;
	}


	location ~ \.php$ {
        	include snippets/fastcgi-php.conf;
        	fastcgi_pass unix:/run/php/php7.0-fpm.sock;
    	}

    	location ~ /\.ht {
        deny all;
    	}

	location /phpmyadmin {
# gives 404 		root /usr/share/phpmyadmin;
  		root /usr/share;
  		index index.php;
  		try_files $uri $uri/ =404;

  	location ~ ^/phpmyadmin/(doc|sql|setup)/ {
    		deny all;
  		}

  	location ~ /phpmyadmin/(.+\.php)$ {
    		fastcgi_pass unix:/run/php/php7.0-fpm.sock;
    		fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    		include fastcgi_params;
    		include snippets/fastcgi-php.conf;
  		}
 	}



    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/tools.site.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/tools.site.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot


    if ($scheme != "https") {
        return 301 https://$host$request_uri;
    } # managed by Certbot

}

```


ls -l /usr/share/nginx/html/
total 4
-rw-r--r-- 1 root root 612 Jan 31  2017 index.html
lrwxrwxrwx 1 root root  22 Dec 12 20:41 phpmyadmin -> /usr/share/phpmyadmin/


If I go to [https://tools.site.com/phpmyadmin](https://tools.site.com/phpmyadmin) I get the login prompt for phpmyadmin. Next page brings me to [https://tools.site.com/index.php?token=***](https://tools.site.com/index.php?token=***)  
404 Not found, because the phpmyadmin is missing.
If I correct that in the URL to [https://tools.elmit.com/](https://tools.elmit.com/)**phpmyadmin**/index.php?token=***    I am in.

However, its not complete!!! I have no Permission tab to setup a new user + database.

How do I fix that?

---

### Post by Kirboosy on 2017-12-12
I would change the permissions of your html files to *www-data*. By default Nginx runs on www-data.

```
chown -R www-data:www-data /usr/share/nginx/html/*
```

Restart the nginx and see if there are any changes in results

Also small suggestion. Why not redirect traffic to HTTPS/SSL rather than juggling between the two? Under your HTTP options you could use the following
```

location / {
     return 301 https://tools.site.com$request_uri;
}

```

Hope that helps!
~Caboose

---

### Post by QIII on 2017-12-12
Just as a suggestion in the interest of security:

Having phpMyAdmin accessible from your web interface adds an attack surface.  I sometimes get hundreds of reported attempted hacks trying to use phpMyAdmin as a point of entry.  Furthermore, when you are in the middle of using phpMyAdmin when accessing your site from the web, you are even more vulnerable.  If your database is directly exposed, it will be hacked.

I don't even have phpMyAdmin installed on my web servers.  Instead, I use MySQL Workbench tunneled over SSH from my machine at home, or just use the terminal over ssh for simple stuff.

---

### Post by ELMIT on 2017-12-12
I did change chown -R www-data:www-data /usr/share/nginx/html/* but it had no effect. After login, I come to the site without 'phpmyadmin'

---

### Post by ELMIT on 2017-12-12
I never heard about mysql workbench. I just have installed it. Is there a users guide? - found it at [https://www.mysql.com/products/workbench/](https://www.mysql.com/products/workbench/)

As I can see it covers what I actually wanted to do, add a user, add a database. 
One more I need, to enter/edit data. That was for me the main reason to install phpmyadmin. Maybe there is another quick tool available.

---

### Post by QIII on 2017-12-12
Here's what you are looking for:

[https://dev.mysql.com/doc/refman/5.7/en/](https://dev.mysql.com/doc/refman/5.7/en/)

There's nothing really unexpected or difficult in entering/manipulating/updating data as soon as you get the hang of it from the documentation.  

Cheers!

---

### Post by ELMIT on 2017-12-13
I switched to workbench!
Thanks for telling me about it.

---

### Post by QIII on 2017-12-13
Welcome!

We're here if you have problems, of course!

---

