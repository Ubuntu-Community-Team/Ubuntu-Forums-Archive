---
title: "What should an NGINX phpPgAdmin config file look like?"
date: 2015-01-24
forum: General Help
---

### Post by stevenm-wills on 2015-01-24
I'm trying to get phpPgAdmin to work with NGINX

If you install Apache you get /etc/apache2/conf.d/phppgadmin. 

When you install NGINX you get /etc/nginx/conf.d/ and there isn't automatically a config file. So I need to make one.

I was trying and trying to get phpPgAdmin to work with NGINX. I couldn't get it so I wanted to see how Apache was different. So I repeated my steps, substituting NGINX with Apache.

I installed postgresql, postgresql-contrib, phppgadmin, and Apache.

I made my symlink to work with Apache.

```
[COLOR=#000000][FONT=monospace]ln [/FONT][/COLOR][COLOR=#000000][FONT=monospace]-s[/FONT][/COLOR][COLOR=#000000][FONT=monospace] /usr/share/phppgadmin /var/www/html/phppgadmin[/FONT][/COLOR]
```

And boom! It just worked. I was able to go to 10.0.1.22/phppgadmin

So here's my problem. I can't seem to find a good example of a phppgadmin NGINX config file. Can someone please demonstrate one, or provide a link to one?

I tried the following, but it didn't work.

```

server {
listen          80;
server_name     localhost;


error_log       /var/log/postgre.yourdomain.com_error.log error;


root /usr/share/nginx/html/phppgadmin;
index index.php;


location / {
allow   all;    
}


location ~ .php$ {
include phpfpm_params;
allow   all;
}


location ~ /\.ht {
deny all;
}
}

```

I'm able to install NGINX, create a symlink and then get a 403 page at 10.0.1.22/phppgadmin. So all I need is an NGINX config file.

And before you suggest it, yes, I am doing my NGINX symlink like

```
[COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono][FONT=monospace]ln [/FONT][/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono][FONT=monospace]-s[/FONT][/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono][FONT=monospace] /usr/share/phppgadmin /usr/share/nginx/html/phppgadmin[/FONT][/FONT][/COLOR][/COLOR]
```

Thanks for reading.

---

