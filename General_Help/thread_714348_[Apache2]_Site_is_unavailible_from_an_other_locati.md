---
title: "[Apache2] Site is unavailible from an other location than localhost"
date: 2008-03-03
forum: General Help
---

### Post by LeDieu on 2008-03-03
Hello,

I am currently busy with my apache server.
But the problem is that i cant access my site from a external domain.
The site is only availible from localhost.

When i try to access my server with a external request i get the error: 

Not Found

The requested URL / was not found on this server.

But when i acces it from [http://localhost](http://localhost) it works perfectly.

I have added in my /etc/hosts file "127.0.0.1 <domain>" and <domain> is the domain i am using.
But this seems to have no effect.

Does anyone have a sollution for this problem?

Greetz,
LeDieu

---

### Post by SpaceTeddy on 2008-03-04
mhm... there is not enough information to acctually solve this problem :)

please post the content of your virtual host setup (if you have done any). The virtual hosts are found in /etc/apache2/sites-enabled (enabled because the disabled ones will not answer to anything anyway)

also, how if your computer running the apache connnected to the internet ? is there a modem/router inbetween ? what ip address does it have (also, please include the output of ifconfig)

there are two guesses i would take here as to why it does not work...
1.) you have a router inbetween which does not forward the requests form the internet
2.) you have a virtual host definition that will only answer on the ip/hostname for the localhost

let's hope we can figure out

---

### Post by LeDieu on 2008-03-04
I dont think it is my router. All the ports i forward are forwarded correctly.
So here is my printout of my vitrualhost file.
NameVirtualHost ledieu.ath.cx:80
> 
<VirtualHost ledieu.ath.cx:80>
        ServerName ledieu.ath.cx
        ServerAlias ledieu.ath.cx
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/MyBlog
        <Directory /etc/apache2/site-enable>
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # RedirectMatch ^/$ /MyBlog/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

I hope this helps.

Greetz,
LeDieu

---

### Post by Oldsoldier2003 on 2008-03-04
> **LeDieu said:**
> I dont think it is my router. All the ports i forward are forwarded correctly.
So here is my printout of my vitrualhost file.
NameVirtualHost ledieu.ath.cx:80


I hope this helps.

Greetz,
LeDieu
try connecting using the external ip address assigned to the server. if that works then its dns related

---

### Post by SpaceTeddy on 2008-03-04
if your /etc/hosts configures the name ledieu.ath.cx on the loopback device, then this configuration will only work on the loopback, since it is only bound there. this would mean that this line
```
<VirtualHost ledieu.ath.cx:80>
```
acctually means 
```
<VirtualHost 127.0.0.1:80>
```
meaning that the server will only answer with this virtual host on that network card.

try this virtual host configuration instead:
```
<VirtualHost *:80>
```
and it should start working, since it will answer on all devices then (it will still only respond to the name name, not the ip though)

---

### Post by LeDieu on 2008-03-04
When i use your solution i get redirected to "localhost".
So if i type "ledieu.ath.cx" my browser gets redirected to "http://localhost".
Very strange

---

### Post by SpaceTeddy on 2008-03-05
mhm... very strange. that would mean the apache is rewriting the hostname... what happens if you take the host information out of the /etc/hosts file completely ? does it work then ?

otherwise, i am running out of ideas... really...
sorry

---

### Post by LeDieu on 2008-03-06
Well.... that doesnt work ether so i think I just reinstall my server. It is a old version of ubuntu to so not a big problem.
Thanks for your help thow.

Greetz,
LeDieu

---

### Post by steveneddy on 2008-03-06
Are you on a DSL line or is your connection static?

If it is a DSL, the IP address changes. They call this Dynamic IP.

Static IP is a non changing IP address.

You have to have software installed if you have DSL to tell the DNS servers what your IP address is.

dyndns.org is a good place to learn about this service.

I believe I use **ddclient** to tell the servers what my IP address is.

My router port 80 is open and ddclient runs at startup.

This is the way I use to access my server while not at home. I can type in my address, much like your 

**ledieu.ath.cx**

address, and I have access to all of my files and a web server.

So, a DSL connection or any dynamic, or changing, IP address may need additional software installed on the PC to complete your task.

Just an added note, my Linksys router does this same thing, and I utilize the router software **and** ddclient to update my DNS server at dyndns.com.

---

