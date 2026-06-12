---
title: "apache virtual host file for ruby application"
date: 2008-03-27
forum: General Help
---

### Post by mickey13 on 2008-03-27
Hi all,

I'm trying to set up my Ruby application to work on my apache2 server.  I'm pretty sure I have everything installed that I need.  I feel like the problem is related to my virtual host file.  I was able to have the default Ruby on Rails file show up as my website, but I don't know how to tell apache to look at my welcome page located at:

/var/www/example.com/app/views/welcome/index.html.erb.

I've tried various things in my virtual host file, but no luck so far.  Here's a snippet of my virtual host file:

<VirtualHost *>
ServerName [www.example.com](www.example.com)
ServerAlias example.com

DocumentRoot /var/www/example.com/public

<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>

<Directory /var/www/example.com/public/>
Options Indexes FollowSymLinks Multiviews
AllowOverride all
Order allow,deny
allow from all
</Directory>

...

</VirtualHost>

Thanks in advance for the help.
Mickey

---

### Post by nsche on 2008-03-28
You probably need to get rid of public/index.html

---

### Post by mickey13 on 2008-03-29
Thanks, I tried that and rest of the files in the public/ directory are listed on my website.  I think there might be something I need to do with the config/routes.rb file, but I don't have a good understanding of what to do.  Any ideas?  Thanks again in advance.

---

