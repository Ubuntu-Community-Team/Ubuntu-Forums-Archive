---
title: "Cant access apache document root?"
date: 2014-07-02
forum: General Help
---

### Post by sameermw on 2014-07-02
My apache document root locate in **/var/www** and i created a directory called **testwp** on **/var/www**. I changed some privileges
```



[LIST]
[*]sudo chown -R $USER:$USER /var/www/testwp
[*]sudo chmod 755 /var/www/testwp
[/LIST]

```

but i cant access that directory from my web browser > [http://localhost/testwp](http://localhost/testwp) and it says[INDENT][B]404 Not Found The requested URL /testwp was not found on this server.

[/B]This is my site-available configuration
```
<VirtualHost *:80>    
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/testwp
    <Directory />
            Options FollowSymLinks
            AllowOverride None
        </Directory>
        <Directory /var/www/testwp>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            allow from all
        </Directory>
</VirtualHost>

```[/INDENT]
How can i access like that? can i do that? please help me. thanks

---

### Post by sameermw on 2014-07-03
Any way i solved my problem thanks to an expert outside the forum.

here is the solution,

```
ServerAdmin webmaster@localhost
    DocumentRoot **/var/www**
    <Directory />
            Options FollowSymLinks
            AllowOverride None
    </Directory>
    <Directory **/var/www/**>
            Options Indexes FollowSymLinks MultiViews
            AllowOverride None
            Order allow,deny
            allow from all     </Directory> . . . 
```

That's why it is not working. Change it to /var/www. Currently [http://localhost/testwp](http://localhost/testwp) refers to /var/www/testwp/testwp and [http://localhost](http://localhost) refers to /var/www/testwp

---

