---
title: "Trouble setting up SSL on Nginx proxying to Apache"
date: 2014-10-01
forum: General Help
---

### Post by bphillips2 on 2014-10-01
I am running a few internal office sites on an ubuntu server.  I have a need for these sites to be secure.  I purchased a multi-domain certificate for these sites and have two of them working as intended with the certificate but am having trouble with the third.  I am using the same settings in my nginx/sites-available files and my apache2/sites-available files.  But when I set it up I either get a 404 error or the subdomain address redirects to one of the other internal sites hosted on the server.

This is what I have in my nginx/sites-available/zurmo file for our internal CRM, Zurmo.  This configuration works as intended with a working SSLto demonstrate a working configuration. website is crm.bowgroup.com

```

server {  listen 80;
  server_name crm.bpwgroup.com www.crm.bpwgroup.com;
  access_log /var/log/nginx/crm.bpwgroup.log;
  rewrite ^ https://$server_name$request_uri;  # enforce https


  location / {
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $http_host;
    proxy_set_header X-NginX-Proxy true;
 
    set $portNum 1918;
 
    proxy_pass http://127.0.0.1:$portNum;
    proxy_redirect off;
  }


}


server {
  listen 443;
  ssl on;
  server_name crm.bpwgroup.com www.crm.bpwgroup.com;
  ssl_certificate /etc/ssl/certs/ssl-bundle.crt;
  ssl_certificate_key /etc/ssl/myserver.key;


  access_log /var/log/nginx/crm.bpwgroup.log;
```

And my Apache2/sites-available/default file for this site

```

server {  listen 80;
  server_name crm.bpwgroup.com www.crm.bpwgroup.com;
  access_log /var/log/nginx/crm.bpwgroup.log;
  rewrite ^ https://$server_name$request_uri;  # enforce https


  location / {
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $http_host;
    proxy_set_header X-NginX-Proxy true;
 
    set $portNum 1918;
 
    proxy_pass http://127.0.0.1:$portNum;
    proxy_redirect off;
  }


}


server {
  listen 443;
  ssl on;
  server_name crm.bpwgroup.com www.crm.bpwgroup.com;
  ssl_certificate /etc/ssl/certs/ssl-bundle.crt;
  ssl_certificate_key /etc/ssl/myserver.key;


  access_log /var/log/nginx/crm.bpwgroup.log;
```


The site I'm having trouble with (a wordpress site) works just fine, but without the SSL, using this configuration in /nginx/sites-available/openatrium.  site is ap.bpwgroup.com

```

server {  listen 80;
  server_name ap.bpwgroup.com www.ap.bpwgroup.com;
  access_log /var/log/nginx/ap.bpwgroup.log;
  location / {


    client_max_body_size 20M;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $http_host;
    proxy_set_header X-NginX-Proxy true;
    set $portNum 8083;


    proxy_pass http://127.0.0.1:$portNum;
}






  }
```

And this code in apache2/sites-available/atrium

```

<VirtualHost *:8083>

        DocumentRoot /home/justin/agent-portal/wordpress/


        Alias /openatrium/ /home/justin/agent-portal/wordpress/
        <Directory />
                Options FollowSymLinks
        AllowOverride None
        </Directory>


        <Directory /home/justin/agent-portal/wordpress/>
                Options +FollowSymLinks
                AllowOverride All
                order allow,deny
                allow from all
        </Directory>




</VirtualHost>
```

But no matter what I add to the nginx/sites-available/openatrium file I can not get the SSL to work and the page (ap.bpwgroup.com) to direct to where it needs to go (home/justin/agent-portal/wordpress).  It either shows a SSL and a 404 error or it redirects to the other site on the server (crm.bpwgroup.com).  Can anyone help point me in the right direction on how to do this?

Thanks,

---

