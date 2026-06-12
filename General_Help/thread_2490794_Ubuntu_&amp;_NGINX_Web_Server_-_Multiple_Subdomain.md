---
title: "Ubuntu &amp; NGINX Web Server - Multiple Subdomains to Log In To phpMyAdmin"
date: 2023-09-15
forum: General Help
---

### Post by aaroncatolico1 on 2023-09-15
[COLOR=#232629][FONT=-apple-system]I'm trying to have 2 separate subdomains from 2 different websites have access to logging into the same phpMyAdmin.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I'm not sure how to set up the phpmyadmin.conf file so that NGINX knows how to forward both subdomains to the phpmyadmin login page.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Here's what my Nginx Server Block for the phpmyadmin.conf file looks like, located at ***/etc/nginx/conf.d/phpmyadmin.conf***[/FONT][/COLOR]
```
server {
listen 80;
listen [::]:80;
server_name pma.website1.com;
root /usr/share/phpmyadmin/;
index index.php index.html index.htm index.nginx-debian.html;

access_log /var/log/nginx/phpmyadmin_access.log;
error_log /var/log/nginx/phpmyadmin_error.log;

location / {
try_files $uri $uri/ /index.php;
 }

location ~ ^/(doc|sql|setup)/ {
deny all;
 }

location ~ \.php$ {
fastcgi_pass unix:/run/php/php7.4-fpm.sock;
fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
include fastcgi_params;
include snippets/fastcgi-php.conf;
 }

location ~ /\.ht {
deny all;
 }
}
[COLOR=#232629][FONT=-apple-system]So, I'm[/FONT][/COLOR]
```[COLOR=#232629][FONT=-apple-system] wondering how I can have both pma.website1.com subdomain and pma.website2.com subdomain both redirect to the main phpmyadmin log in page. Any support would be appreciated.[/FONT][/COLOR]

---

### Post by TheFu on 2023-09-16
phpMyAdmin is constantly under attack.  I see hundreds of attempts here.  

So, I'd strongly recommend that whatever you do, ensure that only your real client can have access to that website.  It would probably be best to only allow localhost connections on the webserver listener AND use an ssh tunnel from your real workstation into the remote server for access to that entire webapp or any other webapps.  We shouldn't make it easy for our systems to be cracked and taken over.

As for redirecting requests, I'd use a rewrite rule.  Those are pretty easy. [https://httpd.apache.org/docs/2.4/rewrite/intro.html](https://httpd.apache.org/docs/2.4/rewrite/intro.html)

---

### Post by aaroncatolico1 on 2023-09-16
[SIZE=3]Actually, this will be for a desktop application that my users will need to query the database with remote logins.
I'm rebuilding the whole server and have never had any problems in the past with the system I built. For each website, I'd like to have it to where I can log in from a subdomain for each website.
For example, website1.com will have it's own subdomain to log in to phpmyadmin via pma.website1.com. Then, I'll have another website that has it's own database with website2.com and have it to where I can log in to phpmyadmin from it's subdomain at pma.website2.com.

This has to be configured in NGINX, NOT Apache.
[/SIZE]



> **TheFu said:**
> phpMyAdmin is constantly under attack.  I see hundreds of attempts here.  

So, I'd strongly recommend that whatever you do, ensure that only your real client can have access to that website.  It would probably be best to only allow localhost connections on the webserver listener AND use an ssh tunnel from your real workstation into the remote server for access to that entire webapp or any other webapps.  We shouldn't make it easy for our systems to be cracked and taken over.

As for redirecting requests, I'd use a rewrite rule.  Those are pretty easy. [https://httpd.apache.org/docs/2.4/rewrite/intro.html](https://httpd.apache.org/docs/2.4/rewrite/intro.html)

---

### Post by #&amp;thj^% on 2023-09-16
> **aaroncatolico1 said:**
> [SIZE=3]Actually, this will be for a desktop application that my users will need to query the database with remote logins.
I'd like to have it to where I can log in from a subdomain for each website.
This has to be configured in NGINX, NOT Apache.
[/SIZE]
have you looked here: [https://adamtheautomator.com/nginx-subdomain/](https://adamtheautomator.com/nginx-subdomain/)
And one a little more current: [https://blog.logrocket.com/how-to-build-web-app-with-multiple-subdomains-nginx/](https://blog.logrocket.com/how-to-build-web-app-with-multiple-subdomains-nginx/)
You will have to tailor it for your use. (I will be of no help here though)

---

### Post by dragonfly41 on 2023-09-16
My thoughts are to use Laravel as front end and use Laravel subdomain routing.

I admit that I tested this idea in a chatGPT session (phind.com) and it seems to fly.

P.S. this was the query in browser:

Requirement: Ubuntu & NGINX Web Server - Multiple Subdomains to log into phpMyAdmin. Can Laravel routing be used for this NGINX/PHP architecture? How secure is PHP/MyAdmin?

---

### Post by TheFu on 2023-09-16
> **aaroncatolico1 said:**
>  This has to be configured in NGINX, NOT Apache.

Ooops.  Sorry.  I actually use nginx mainly, but whenever I think of php users, I think of apache for some reason. Don't know why.

I have no idea how to setup nginx to use php, but I use nginx for static websites, as a front-end, TLS termination point and load balancer for other webapps.  I have each as a subdomain and use SNI for nginx to send traffic to the correct back-end webapp.  Effectively, the server_name line is what determines the SNI.  Setup the per-subdomain nginx config file something like this:

```
upstream webapp-proxy  {
        server 172.22.22.4:8181;
}

server {
   server_name   site1.doman.lan; 
   listen 80; 
   location / {
                try_files index.php index.html @webapp-proxy ;
    }

   location @webapp-proxy {
    ##### php stuff here, I guess?  Probably 10-20 config lines here with the proxy_pass as the last linea
    proxy_pass http://webapp-proxy ;
   }
}
```

I really don't know how for a php webapp.  There are many different ways with nginx. Probably something much simpler than I use. This is probably more confusing than helpful.

I'd setup another config file just like it with a different server_name for the other subdomain and point the backend to either a different server or different port where I've setup the other instance.

I usually need to load balance, so need caching on nginx, TLS termination and multiple back-end servers.  For my code, I tend to use PSGI webapps that can be easily scaled.  Nginx is just a CSS, JS, and static content server with plackup/starman as the actual webapp server(s).  I use lots of include lines to add restrictions, log formats, strict-transport, and block unwanted self-reported clients.

The idea of giving end users access to phpmyadmin scares me. Hopefully, they are all DBAs, but only you know what's best for the situation.  I hope you are monitoring the logs to see any cracker attempts.

---

### Post by dragonfly41 on 2023-09-16
Here is the full dump of reply from ChatGPT query.

ANSWER | GPT-3.5-TURBO MODEL
Yes, Laravel routing can be used with NGINX as the web server on Ubuntu. Here's a step-by-step guide to achieve this:
Install and configure Laravel with NGINX on Ubuntu. You can follow the instructions in digitalocean.com for detailed steps on setting up Laravel with NGINX.
Create or point your subdomains to the server's IP address. This can be done by modifying the DNS records of your domain to include the subdomains. You can refer to serverfault.com for more information on creating DNS records for subdomains.
Configure NGINX server blocks to handle the subdomains. Server blocks allow you to define separate configurations for different domains or subdomains. You can follow the instructions in albertogrespan.com to set up server blocks for your subdomains.
Set up Laravel routing for each subdomain. Laravel provides a powerful routing system that allows you to define routes for different URLs. You can create separate route files for each subdomain and define the routes specific to that subdomain. Here's an example of how you can define routes for a subdomain in Laravel:
// routes/subdomain.example.com.php
Route::domain('subdomain.example.com')->group(function () {
    // Routes for subdomain.example.com
    Route::get('/', function () {
        return 'Welcome to subdomain.example.com';
    });
    Route::get('/login', function () {
        return 'Login page for subdomain.example.com';
    });
    // Other routes for subdomain.example.com
});
You can create similar route files for each subdomain and include them in your main routes/web.php file using the Route::group() method.
Configure phpMyAdmin with NGINX. If you also want to set up phpMyAdmin for each subdomain, you can follow the instructions in cloudbooklet.com to configure phpMyAdmin with NGINX.
By following these steps, you can use Laravel routing to handle multiple subdomains with NGINX as the web server on Ubuntu.
SOURCES
favicon-stackoverflow.com
stackoverflow.com > questions > 59653445 > hosting-a-laravel-app-with-multipule-subdomains-on-nginx-vps-host
php - Hosting a Laravel app with multipule subdomains on nginx vps host ...
Hosting a Laravel app with multipule subdomains on nginx vps host Ask Question Asked 3 years, 8 months ago Modified 3 years, 8 months ago..
favicon-stackoverflow.com
stackoverflow.com > questions > 28659068 > laravel-routes-overwriting-phpmyadmin-path-with-nginx
Laravel routes overwriting phpmyadmin path with nginx
Just make sure to adjust the three "root" locations to the folder where your "phpmyadmin" folder is in (the location of my phpmyadmin folder is..
favicon-www.digitalocean.com
[www.digitalocean.com](www.digitalocean.com) > community > tutorials > how-to-install-and-configure-laravel-with-nginx-on-ubuntu-20-04
How To Install and Configure Laravel with Nginx on Ubuntu 20.04 (LEMP ...
If you haven&#8217;t set this up yet, you can follow steps 1 to 3 of our guide on How to Install Nginx, MySQL and PHP..
favicon-medium.com
medium.com > @mahmud_kuet > sub-domain-routing-in-laravel-with-nginx-ubuntu-16-04-68e9d08a9776
Sub-domain routing in Laravel with Nginx In Ubuntu - Medium
Sub-domain routing in Laravel with Nginx In Ubuntu Step #1 &#8212; (Nginx configuration): Create a virtual host block in Nginx. Go to /etc/nginx/sites-available/ . Ru..
favicon-www.digitalocean.com
[www.digitalocean.com](www.digitalocean.com) > community > tutorials > how-to-install-and-secure-phpmyadmin-with-nginx-on-an-ubuntu-20-04-server
How To Install and Secure phpMyAdmin with Nginx on an Ubuntu 20.04 ...
Prerequisites In order to complete this guide, you will need: A server running Ubuntu 20.04. This server should have a non-root user with administrative privile..

---

### Post by TheFu on 2023-09-16
Whenever I ask an AI engine for answers, they are close and reasonable, but never actually work via copy/paste.  Beware.

---

### Post by dragonfly41 on 2023-09-17
I agree that caution is needed. Always ask to compare your own ideas. Not following advice blindly. And often I have to correct their assumptions by asking .. "But consider this fact ... "  They do not yet pass the Turing test .

But on the matter of using Laravel as routing and authentication engine I think there is consensus.

I get better returns by a series of short, precise questions. And I fire up a Heroku dyno to be a testbed.

... adding this tutorial ..

[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-laravel-with-nginx-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-laravel-with-nginx-on-ubuntu-20-04)

---

