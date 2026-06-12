---
title: "Apache2 IP address is shown in address bar instead of domain address"
date: 2018-07-04
forum: General Help
---

### Post by otid91 on 2018-07-04
[COLOR=#242729][FONT=Arial]I'm pretty new with apache and confirguring websites. Earlier this week, I bought a domain name with go daddy, call it [www.exemple.com]("http://www.exemple.com"). When I try to access my website using my domaine [www.exemple.com]("http://www.exemple.com"), the redirection to my server works fine, but than the domaine name is changed with my server ip address.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm not certain if this is a godaddy or apache problem. but I'm pretty sure this is an apache configuration that I need to set.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]How can I say to apache to display may domaine name instead of my ip address ?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Here is the configuration of my virtualhost
[/FONT][/COLOR]
> Listen 5000

<VirtualHost *:5000>
     DocumentRoot /var/www/example
     ServerName example.com
     ServerAlias [www.example.com]("http://www.example.com")
</VirtualHost>

[COLOR=#242729][FONT=Arial]Also, I'm trying to access my website from outside (Using my own machine, not the server)
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The virtualhost is in a new site.conf inside sites-avalaible and enabled with a2ensite and displayed in sites-enabled
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My 000-default.conf only contain
[/FONT][/COLOR]
> ServerName localhost

[COLOR=#242729][FONT=Arial]to prevent a warning when using apache2ctl -S
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any help would be really appreciate, I searched for hours on google and have not found a working solution[/FONT][/COLOR]

---

