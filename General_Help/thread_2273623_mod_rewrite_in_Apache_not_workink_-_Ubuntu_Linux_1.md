---
title: "mod_rewrite in Apache not workink - Ubuntu Linux 14.04.2"
date: 2015-04-14
forum: General Help
---

### Post by razvan6 on 2015-04-14
Hi there to all, 
I am new here and i am not professional user, let`s say medium.
I have my own vps, installed Ubuntu Linux 14.04.2 and Lamp Server, i want to host some domains.
Ok, the permalinks not working on websites.
Examle: [www.website.come/news]("http://www.website.come/news") is not working. I have enabled permalinks(wordpress) from control pannel and nothing..
Ok..next on root:
sudo a2enmod rewrite
sudo service apache2 restart


Module rewrite already enabled. 

Next i have opened apache2.conf and put this code: (but then my website is not working, [h=1]Forbidden[/h][COLOR=#000000][FONT=Times New Roman]You don't have permission to access / on this server.[/FONT][/COLOR]

<Directory /var/www/>
            Options Indexes FollowSymLinks MultiViews
            # changed from None to FileInfo
            AllowOverride FileInfo
            Order allow,deny
            allow from all
    </Directory>

Then running a2dismod negotiation and nothing...

Help???

---

### Post by dragonfly41 on 2015-04-14
Just a few questions for clarification ...

What version apache?

Note that apache 2.4.* uses these directives

            AllowOverride All
            Require all granted

and Apache 2.4.* docroot is /var/www/html .. not ..  /var/www

Also check site ownership www-data:www-data for DocumentRoot

What is the full virtualhost conf configuration in /etc/apache2/sites-available

Is [www.website.com](www.website.com)[COLOR=#ff0000]**e**[/COLOR]/news a typo?  should be [www.website.com/news](www.website.com/news)

Have you enabled virtualhost conf file .. sudo a2ensite myhost

What do you see running apachectl configtest?

should be "syntax ok"

---

### Post by razvan6 on 2015-04-14
i have installed from 0 ubuntu [COLOR=#393939][FONT=arial]Ubuntu Linux 12.04.5
when i wrote  [/FONT][/COLOR]sudo a2enmod rewrite
Then restart the apcahe2 using

service apache2 restart

now i'm receiving 
**Forbidden**

[COLOR=#000000][FONT=Times New Roman]You don't have permission to access / on this server.
[I]Apache/2.2.22 (Ubuntu)

My installation of ubuntu is in automatic from vps cpannel, so where is now the problem? doh

LE: with [/I][/FONT][/COLOR]sudo a2dismod rewrite
the website is working, permalinks no..

---

### Post by razvan6 on 2015-04-15
SOLVED!!!!!
/etc/apache2/sites-available/www.mydomain.com.conf
allow from all
Options All (was None)
Require all granted

OLE!!!!!!

---

