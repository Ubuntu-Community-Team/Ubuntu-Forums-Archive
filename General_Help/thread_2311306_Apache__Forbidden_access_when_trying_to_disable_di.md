---
title: "Apache : Forbidden access when trying to disable directory listing."
date: 2016-01-26
forum: General Help
---

### Post by akshay-sulakhe on 2016-01-26
Hello friends,

I recently installed an ecommerce framework called Showpare on  Apache. Now that the installation is complete, when I start the website,  it was showing me Indexes of all the files present in /var/www/html,  so I removed Indexes, and now I am getting a forbidden error. What can I  do, the suggestions on other  forums are not helping, tried already. 


  sites-enabled/000-default :
```


<VirtualHost *:80>
 DocumentRoot /var/www/html/
        <Directory />
                  Options FollowSymLinks
                AllowOverride none
       </Directory>
        <Directory /var/www/html/>
                Options MultiViews FollowSymLinks SymLinksIfOwnerMatch Includes ExecCGI
                AllowOverride all
                Order allow,deny
                allow from all

        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>
```

When I tried to a2dismod autoindex, then I get 404. Why is it so problematic to disable Directory_listing? How can I achieve it?

---

### Post by dragonfly41 on 2016-01-26
Try placing a .htaccess hidden file at DocumentRoot

[http://www.htaccess-guide.com/disable-directory-listings/](http://www.htaccess-guide.com/disable-directory-listings/)

also remove closing slash .. [COLOR=#000000][FONT=Ubuntu Mono]DocumentRoot /var/www/html[/FONT][/COLOR][COLOR=#ff0000][FONT=Ubuntu Mono]**/**[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]

---

### Post by akshay-sulakhe on 2016-01-26
Hi,

I changed the sites-enabled/000-default to look like this :

 ServerAdmin webmaster@localhost
        DocumentRoot /var/www
         <Directory />
                Options FollowSymLinks
                AllowOverride None
                Require all granted
        </Directory>
        <Directory /var/www >
                Options FollowSymLinks MultiViews
                AllowOverride All
                Require all granted
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>


And added .htaccess with IndexIgnore *. Now I keep getting forbidden error. If I add Indexes in VirtualHost now, I see index page, but nothing in Index.

---

### Post by dragonfly41 on 2016-01-26
I'm fairly sure (at least on my Ubuntu 14.04) that DocumentRoot should be /var/www/html
... without closing slash
not /var/www

[later edit .. correction]
Actually I now see that I have my multiple virtualhosts directories in /var/www/vhosts

and the localhost content is in /var/www/html

So DocumentRoot specifies the path to each virtualhost site.

Why not add some error logging?

---

### Post by akshay-sulakhe on 2016-01-26
Hi,

I purged apache2 and re-installed it. My root is now /var/www/html. I tried multiple configurations, but still no success with the forbidden problem. What should I do?

Config : 

   DocumentRoot /var/www/html

  <Directory />
             Options FollowSymLinks MultiViews
            AllowOverride None
            Require all granted
    </Directory>
    <Directory /var/www/html >
Options -Indexes
      Require all granted
    </Directory>

---

### Post by dragonfly41 on 2016-01-26
> I changed the sites-enabled/000-default to look like this :

Generally you should copy the default 000-default in /etc/apache2/sites-available/000-default.conf and create your custom myvirtualhost.conf file to be edited (i.e. leave 000-default.conf untouched).

then use the command(s) 
a2ensite .. enable site
a2dissite .. disable site

a2ensite myvirtualhost.conf
creates the enabled site into  /etc/apache2/sites-enabled/myvirtualhost.conf

Also add myvirtualhost into /etc/hosts

Here are a few troubleshooting steps (what version apache2 are you running .. 2.4?)

(1) read typical advice here .. 
[http://askubuntu.com/questions/413887/403-forbidden-after-changing-documentroot-directory-apache-2-4-6](http://askubuntu.com/questions/413887/403-forbidden-after-changing-documentroot-directory-apache-2-4-6)
[http://stackoverflow.com/questions/17636389/apache2-virtualhost-403-forbidden](http://stackoverflow.com/questions/17636389/apache2-virtualhost-403-forbidden)

(2) run command apache2ctl -S and report output.

(3) cd /var/www/html

(4) ls -l

(5) check ownership of /var/www/html (apache2 requires www-data:www-data)

There might be some other points I've missed (such as .htaccess).

---

