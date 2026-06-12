---
title: "Try to switch to nginx not working"
date: 2017-10-25
forum: General Help
---

### Post by ELMIT on 2017-10-25
I got a wordpress multisite and have troubles to get it switched to nginx.

For the transition period I use for nginx the port 8000.
The sites without wordpress work already.

```
server {
	listen 8000;
	listen [::]:8000;
	server_name elmit.com ctc.elmit.com cat.elmit.com;
	root /var/www/elmit.com;
	index index.php index.html index.htm index.nginx-debian.html;
	error_log /var/log/nginx/elmit.com-error.log error;
	access_log /var/log/nginx/elmit.com-access.log combined;
	location = /favicon.ico {
		log_not_found off;
		access_log off;
	}
	location = /robots.txt {
		allow all;
		log_not_found off;
		access_log off;
	}
	location / {
		try_files $uri $uri/ /index.php?$args;
	}
	location ~ \.php$ {
		try_files $uri =404;
#		include snippets/fastcgi-php.conf;
		fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
		fastcgi_index index.php;
	}
	location ~ /\. {
		deny all;
	}
}

```

I had to # include snippets/fastcgi-php.conf; otherwise nginx -t complaints 
```
nginx: [emerg] "try_files" directive is duplicate in /etc/nginx/snippets/fastcgi-php.conf:5
nginx: configuration file /etc/nginx/nginx.conf test failed

```

Fyi /etc/nginx/snippets/fastcgi-php.conf:
```
# regex to split $uri to $fastcgi_script_name and $fastcgi_path
fastcgi_split_path_info ^(.+\.php)(/.+)$;

# Check that the PHP script exists before passing it
try_files $fastcgi_script_name =404;

# Bypass the fact that try_files resets $fastcgi_path_info
# see: http://trac.nginx.org/nginx/ticket/321
set $path_info $fastcgi_path_info;
fastcgi_param PATH_INFO $path_info;

fastcgi_index index.php;
include fastcgi.conf;
```


After I get above steps done, I want to use https instead. I will use certbot to get certificates for these 3 sites. Can I do that in one file or do I need to copy the file into 3 files with different servernames ... ?

---

