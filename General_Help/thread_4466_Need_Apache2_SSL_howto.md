---
title: "Need Apache2 SSL howto"
date: 2004-11-15
forum: General Help
---

### Post by dmoulton on 2004-11-15
Can someone point me to an APACHE2 SSL setup howto? 

Thanks

dm

---

### Post by TravisNewman on 2004-11-15
[QUOTE=dmoulton]Can someone point me to an APACHE2 SSL setup howto? 

Thanks

dm[/QUOTE]
 This covers it somewhat in depth.. you can skip a lot of the steps if you don't want to compile things, you can instead install them from synaptic:

[http://ubuntuforums.org/showthread.php?t=3657](http://ubuntuforums.org/showthread.php?t=3657)

The how-to's and reference manuals here are probably the best place to start:
[http://httpd.apache.org/docs-2.0/](http://httpd.apache.org/docs-2.0/)

---

### Post by jdodson on 2004-11-15
[QUOTE=dmoulton]Can someone point me to an APACHE2 SSL setup howto? 

Thanks

dm[/QUOTE]

i just used synaptic to install apache2 and apache2-ssl.

---

### Post by dmatrix on 2004-11-15
Apache + mod_ssl on Ubuntu

- apt-get install apache libapache-mod-ssl
- dpkg-reconfigure libapache-mod-ssl
- fill in all details with your details
- cp /usr/share/doc/libapache-mod-ssl/examples/mod-ssl.conf /etc/apache/conf.d/
- cp /usr/share/doc/libapache-mod-ssl/examples/vhost.conf.gz /etc/apache/conf.d/- cd /etc/apache/conf.d/
- gzip -d vhost.conf.gz
- edit vhost.conf and change all snakeoil references to server. ie. snakeoil-dsa.crt = server.crt
- stop apache
- start apache

---

### Post by jBilbo on 2004-11-16
:-s The above post is for apache1.

A Mini-Howto for apache2: :)

```
apt-get install apache2
apache2-ssl-certificate
```
(and answer the questions)

Now, enable ssl:
```
a2enmod ssl
```

configure ssl:
```
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl
ln -s /etc/apache2/sites-available/ssl /etc/apache2/sites-enabled/ssl 
```
"/etc/apache2/sites-enabled/ssl"  should look like this:

```
NameVirtualHost *:443
<VirtualHost *:443>
(... configure the directories too...)
```
and "/etc/apache2/sites-enabled/default" should look like this:

```
NameVirtualHost *:80
<VirtualHost *:80>
(... configure the directories too...)
```
In /etc/apache2/ports.conf, add Listen 443

In the middle of /etc/apache2/sites-available/ssl file, insert this two lines:

```
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem
```

Hope it helps :)

---

### Post by sb73542 on 2004-11-16
[QUOTE=jBilbo]:-s The above post is for apache1.

A Mini-Howto for apache2: :)

```
apt-get install apache2
apache2-ssl-certificate
```
(and answer the questions)

Now, enable ssl:
```
a2enmod ssl
```

configure ssl:
```
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl
ln -s /etc/apache2/sites-available/ssl /etc/apache2/sites-enabled/ssl 
```
"/etc/apache2/sites-enabled/ssl"  should look like this:

```
NameVirtualHost *:443
<VirtualHost *:443>
(... configure the directories too...)
```
and "/etc/apache2/sites-enabled/default" should look like this:

```
NameVirtualHost *:80
<VirtualHost *:80>
(... configure the directories too...)
```
In /etc/apache2/ports.conf, add Listen 443

In the middle of /etc/apache2/sites-available/ssl file, insert this two lines:

```
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem
```

Hope it helps :)[/QUOTE]
 The XAMPP super package ( [http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)  ) includes Apache + SSL preconfigured, plus everything else you could want in a LAMP environment.  EXTREMELY well done software packaging and configuration, takes about 15 seconds to get up and running.

---

### Post by dmoulton on 2004-11-17
[QUOTE=jBilbo]Hope it helps :)[/QUOTE]

It did! Thank you very much, along with everyone who replied. I appreciate the help.

One thing I'll note is that I pretty much had to gut the <VirtualHost> sections. Here is what I ended up with:
```

<VirtualHost localhost:443>
        DocumentRoot /var/www/
        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem
</VirtualHost>

```

dave

---

### Post by MatthewMetzger on 2004-12-14
I'm in agreement with the person who posted about XAMPP. I wasted hours trying to get apache2 (installed via apt-get ubuntu repository) to work using virtual hosts. It never work intuitively, very complicated. However, virtual hosts are easy to understand and implement in XAMPP. Is is possible that XAMPP could become part of universe or multiverse?

---

### Post by eantoranz on 2005-10-21
jBilbo... thanks for the instructions! It worked just perfect!

---

### Post by theQmaster on 2005-10-28
Anyone know why one would get disconnected when trying to make a https call ?
I installed all as presented in the document, created the certificate but when I call the secure site on 443 I get this error.

[error] [client 127.0.0.1] Invalid method in request \x80g\x01\x03

Any clues ?
theQMaster
Affordable Stock Photography
[http://www.goodstockimages.com](http://www.goodstockimages.com)

---

### Post by mun3kh on 2005-11-07
So many thanks to jBilbo:

He picked up on exactly what the poster asked an provided an the elegant, and it now seems, the proper way to configure apache2 with an ssl site.

Correct, short, sharp and to the point. If you don't write computer books for a living, you should

I Spent ages hunting without doing google:ubuntu apache ssl and I now have apache2 with ssl and subversion module with a working repository, yay!(see this great online book: [http://svnbook.red-bean.com/en/1.1/ch05.html](http://svnbook.red-bean.com/en/1.1/ch05.html))

---

### Post by REBELinBLUE on 2005-11-29
Fantastic, I thought it was going to be a complete PITA after the hastle I had with it on Windows

Now to setup webdav

---

### Post by OneSeventeen on 2005-12-06
Well, I had 3 files from my old server:
mysite.crt
mysite.key
mysite.scrt


I copies the instructions from above for the most part...
I copied the default file to a new file named ssl, then modified it to port 443, then added the following:
```

        SSLEngine       on
        SSLCertificateFile      /etc/apache2/ssl/mysite.crt
        SSLCertificateKeyFile   /etc/apache2/ssl/mysite.key
        SSLCACertificateFile    /etc/apache2/ssl/mysite.scrt
        SetEnvIf User-Agent ".*MSIE.*" nokeepalive ssl-unclean-shutdown

```

When I rebooted the server, it made me type in my passphrase.  I did.
After doing that, if I go to [https://my_url](https://my_url) then I get the page not found errors... (from my browser, not the webserver)

Any ideas?

---

### Post by mgor on 2005-12-06
[https://wiki.ubuntu.com/forum/server/apache2/SSL](https://wiki.ubuntu.com/forum/server/apache2/SSL)

---

### Post by OneSeventeen on 2005-12-06
Well, apparently the only problem I had was I forgot to add:
ServerName foo.example.com

after that, everything worked properly.

(thanks for the link though!  that'll go down in my bookmarks for server stuff)

---

### Post by ddr400 on 2005-12-13
If i want to do my default page start in ssl mode?

when i do [http://site.com](http://site.com) he redirects me to [https://site.com](https://site.com)

How do i do it?

---

### Post by jBilbo on 2005-12-13
[QUOTE=ddr400]If i want to do my default page start in ssl mode?

when i do [http://site.com](http://site.com) he redirects me to [https://site.com](https://site.com)

How do i do it?[/QUOTE]

https is http Secure protocol, it's not the same. If you want http secure, then you must write https (or redirect) in browser... think about it, you can't access to a ftp writing in your browser (for ex.) http...

http port 80
https port 443
ftp port 21

You can change the port but not the protocol name cause the browser will don't understand it.

---

### Post by mgor on 2005-12-14
[QUOTE=ddr400]If i want to do my default page start in ssl mode?

when i do [http://site.com](http://site.com) he redirects me to [https://site.com](https://site.com)

How do i do it?[/QUOTE]

read [https://wiki.ubuntu.com/forum/server/apache2/SSL](https://wiki.ubuntu.com/forum/server/apache2/SSL)
just, remove 'webmail' from the example.

---

### Post by und3rtug4 on 2006-01-14
[QUOTE=jBilbo]:-s The above post is for apache1.

A Mini-Howto for apache2: :)

```
apt-get install apache2
apache2-ssl-certificate
```
(and answer the questions)

Now, enable ssl:
```
a2enmod ssl
```

configure ssl:
```
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl
ln -s /etc/apache2/sites-available/ssl /etc/apache2/sites-enabled/ssl 
```
"/etc/apache2/sites-enabled/ssl"  should look like this:

```
NameVirtualHost *:443
<VirtualHost *:443>
(... configure the directories too...)
```
and "/etc/apache2/sites-enabled/default" should look like this:

```
NameVirtualHost *:80
<VirtualHost *:80>
(... configure the directories too...)
```
In /etc/apache2/ports.conf, add Listen 443

In the middle of /etc/apache2/sites-available/ssl file, insert this two lines:

```
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem
```

Hope it helps :)[/QUOTE]


Great how-to!
Works just fine, no problems!
Thanks dude!
;)

---

### Post by Heliode on 2006-01-19
[QUOTE=jBilbo]:-s The above post is for apache1.

<trim>

Hope it helps :)[/QUOTE]


You rock. Thanks to your post I finially got it working!

---

### Post by TomH on 2006-02-06
I used this guide also and worked excellent!

---

### Post by nihilocrat on 2006-02-09
This is an excellent resource for getting things going, but I'm having trouble trying to use a .pem file other than the self-signed 'apache.pem' I generated.

Specifically, I want to know how to use one of the .pem files from the 'ca-certificates' package (which dumps a bunch of .pem files in /etc/ssl/certs/, which are all symlinks to .crt files in /usr/share/ca-certificates/mozilla/) with my server. I tried the obvious method of just writing the SSL portion of my vhost config like this :
```

# SSL shenanigans
SSLEngine on
SSLCertificateFile /etc/ssl/certs/Thawte_Premium_Server_CA.pem

```

However, when I try that and enable the SSL-enabled site (which worked perfectly fine with apache.pem), apache2 refuses to run after I restart it. After using both '/etc/init.d/apache2 restart' as well as 'apache2ctl restart', both fail to give any sort of error message, except that starting the server again failed.

Is there another step in the process that I've missed?

---

### Post by mgor on 2006-02-09
it might be as simple as apache not havning read permissions for that certificate.

check /var/log/apache2/error.log for errors.

---

### Post by vark on 2007-01-13
Hello,

I also have had a lot of joy from this howto.
 
But the apt-get apache2-ssl-certificate part did not work for me.

So I installed Openssl and followed openssl.org. "related" link to; "ssl certificate howto"

And voila apache 2 on edgy with ssl an a self made certificate.

Tip: you can choose the expiry date for the certificate, default is 365 days.

Regards,

vark

---

### Post by pascalbetz1976 on 2007-01-20
sweet. worked. on my OS-X box it took me about 3 hours to install it (some packages conflicted ). on my ubuntu server... it took me 5 minutes, thanks to this install guide by jBilbo!

thanks

---

### Post by esaym on 2007-02-17
Great how to!

While I am on topic, does anyone know how to just make one part of your site ssl only?  I have a password protected page (ex: [www.mysite.com/securesection](www.mysite.com/securesection) )on my site and I would like to make just that part of my site secure.  I have been reading for about 3 hours now and I haven't found much.  I was still just trying to figure out how to get ssl running and I found this :)

edit:

Wow this is a great how to!  everything works great!  Also I found some info here too: [http://www.vanemery.com/Linux/Apache/apache-SSL.html](http://www.vanemery.com/Linux/Apache/apache-SSL.html)

As far a wanting part of your site ssl and the rest normal http, just set the document root in /etc/apache2/sites-available/ssl to something other then the one in /etc/apache2/sites-available/default.  Then every thing you put in your new ssl root directory will be https.  To automatically redirect the http to https follow this guys advice:  > **mgor said:**
> read [https://wiki.ubuntu.com/forum/server/apache2/SSL](https://wiki.ubuntu.com/forum/server/apache2/SSL)
just, remove 'webmail' from the example.

Just remove the "/webmail" directory and insert what ever directory(s) you want and they will automatically redirect

---

### Post by gvoima on 2007-02-19
> **esaym said:**
> To automatically redirect the http to https follow this guys advice:
There is also a easy way to redirect by using the meta tags http-equiv="refresh" attribute. If you're too lazy to configure apache and restart it ;)

Just put a index.html in your www document root and the meta tag I mentioned of.

---

### Post by kjacks on 2007-03-06
Thanks guys!  This is just what I was looking for!  The default certificate was only valid for 30 days, so my only comment would be to use this command when making the cert:

sudo apache2-ssl-certificate -days 999

---

### Post by danut on 2007-04-24
HELP me PLEASE :(
i have the same site duplicated, one on https and one on http.
i followed these instructions and it works fine both with [http://localhost](http://localhost) and [https://localhost](https://localhost)
but when i try to connect from outside (public IP) it works only with http. https doesn't work, i got "Connection Failed" Error in the browser and nothing is written in the logs.
any suggestion?

---

### Post by jBilbo on 2007-04-24
Maybe you just need to open and forward the 443 port in your router.

---

### Post by danut on 2007-04-24
thanks.. but.. how to check opened ports?
it should be opened but i'm not sure..

---

### Post by eantoranz on 2007-04-24
Check your firewall configuration (linux: iptables -L INPUT -nv) and make sure that the https (tcp 443) is not being blocked by it. If you have a router in the middle between the server and internet, make sure the port os not blocked there and that the packets are being forwarded correctly.

---

### Post by jBilbo on 2007-04-24
Every router is different, so check you router's manual or search in google with your model and keywords "open port". There's a lot of info about it.

---

### Post by danut on 2007-04-24
all router's ports are opened..
with "iptables -L INPUT -nv" i got no entry..

---

### Post by jBilbo on 2007-04-24
The port must be opened and **forwarded **to your host (where Apache2 is).

Try a "telnet your-ip 443" outside of your network and see if it can connect.

---

### Post by danut on 2007-04-24
All the ports are opened and forwarded to the host where Apache2 is.

When i try  "telnet my-ip 443" i got "Impossible to open a connection with host..."

---

### Post by jBilbo on 2007-04-24
One thing:

If you can do a "telnet localhost 443" and connects fine, and then outside your network you do "telnet your-ip 443" and can't connect, it does not seem an apache2 ssl configuration problem for me... but a router/firewall configuration one.
Post here your "netstat -atun" to see if you're listening 443 for 0.0.0.0

---

### Post by danut on 2007-04-24
the only row with 443 is:
tcp6   0   0 :::443   :::*   LISTEN

---

### Post by jBilbo on 2007-04-24
That's good. 

If your router configuration is fine i have no more ideas :(

---

### Post by danut on 2007-04-26
Thank you very much, now it works :)
i just have the last problem and i hope somebody could help me:
outside my network i can connect both with http and https.
inside my network http and https only work with localhost, but i would like to use the Static IP! when i use it, it only works with http. i got "Connection Failed" with https :(
any suggestion?

---

### Post by jBilbo on 2007-04-26
1.- What was the first problem and how did you fix it?

2.- add in /etc/hosts

```
your-static-ip localhost
```

---

### Post by danut on 2007-04-26
MISTAKE!!!

1. i supposed to try outside my network, but i was inside :(

2. i added that line but it doesn't work :(
anyway i don't understand why HTTP works and HTTPS doesn't! it's very strange.. 
in that file i have:
127.0.0.1   localhost
127.0.1.1   server.name.com   server
IP                localhost

---

### Post by riker1968 on 2007-04-28
DANUT

You still have a problem?
And if yes, what is it? 
I think i can help you.
BTW, are you from Rom.?

---

### Post by danut on 2007-04-30
yes :( i'm still in trouble..
i'm not an expert of networking
anyway, between the computer with Apache and internet there's a router
and i have this static IP forwarded to the local IP with all ports opened..

i configured apache with htpps and everything works fine BUT i can't use the static IP with https inside my network.. i would expect both don't work.. but http work with static IP!!!

p.s. i'm not from Romania

---

### Post by gnoobie on 2007-06-28
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/apache2/+bug/77675](https://launchpad.net/ubuntu/+source/apache2/+bug/77675) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[https://launchpad.net/ubuntu/+source/apache2/+bug/77675](https://launchpad.net/ubuntu/+source/apache2/+bug/77675)

check out mlinds entry on this page
I'm going to see if it works

---

### Post by cooper814 on 2007-07-18
Edit:  gah, I click the bug link above me right after posting and see my problem listed, haha.

---

### Post by JakeWins on 2007-08-16
For those of you who, like me, don't have the apache2-ssl-certificate script, use
```
sudo mkdir /etc/apache2/ssl
sudo make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem
sudo chmod a+r /etc/apache2/ssl/apache.pem
```

Also, something I messed up on - make sure that you enter the right name of the server for your certificate - ie. in your apache configuration files, find the line that says 
```
ServerName [random name]
```

I could've sworn I had that to "localhost", but I didn't, and it took me a full day to figure that out :S

---

### Post by wazzup on 2007-11-22
> **jBilbo said:**
> Hope it helps :)

it did. Thanks !

---

### Post by fortran01 on 2008-01-20
On Ubuntu 7.10

(as root)

# aptitude install ssl-cert
# mkdir /etc/apache2/ssl

Hardcoding cert lifetime based on this patch:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=293821#22](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=293821#22)

# make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem

(Answer questions)

# a2enmod ssl

# cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl

Modify it so it looks something like this

```
NameVirtualHost *:443
<virtualhost *:443>
        ServerAdmin webmaster@localhost

        SSLEngine On
        SSLCertificateFile /etc/apache2/ssl/apache.pem

        DocumentRoot /var/www/
        <directory />
                Options FollowSymLinks
                AllowOverride None
        </directory>

        <directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                # Commented out for Ubuntu
                #RedirectMatch ^/$ /apache2-default/
        </directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </directory>

</virtualhost>

```

# sudo a2ensite ssl

don't forget to modify /etc/apache2/sites-available/default

```
NameVirtualHost *:80
<virtualhost *:80>
```

---

### Post by billykaka on 2008-01-23
I am new to Linux and apache and ALthough I have been able to follow the directions and get everthing to work i stil have been unable to figure out how to prepare a cert request from apache. I mean if i wanted to get a cert from a known CA i need a cert request, any ideas on how to prepare that? I appreciate any help i can get

---

### Post by fortran01 on 2008-01-24
[http://wiki.cacert.org/wiki/SubmitCsr](http://wiki.cacert.org/wiki/SubmitCsr)

---

### Post by ispyisail on 2008-01-30
Question about "Fortran01" Ubuntu 7.10 post

Can we clarify?

> Hardcoding cert lifetime based on this patch:
[http://bugs.debian.org/cgi-bin/bugre...?bug=293821#22](http://bugs.debian.org/cgi-bin/bugre...?bug=293821#22)

Are we supposed to cut and past the code (see below) into the file **make-ssl-cert.patch** which will create a certificate when this code is executed > make-ssl-cert /usr/share/ssl-cert/ssleay.cnf /etc/apache2/ssl/apache.pem which will  extend the certificate life?

If this is the case this step would be optional?


```
diff -irbwu ssl-cert-1.0.14/debian/templates ssl-cert-1.0.14.0.olivier.0/debian/templates
--- ssl-cert-1.0.14/debian/templates    2006-05-18 14:02:20.000000000 +0200
+++ ssl-cert-1.0.14.0.olivier.0/debian/templates        2007-02-15 11:49:29.000000000 +0100
@@ -46,3 +46,9 @@
 Template: make-ssl-cert/title
 Type: title
 _Description: Configure an SSL Certificate.
+
+Template: make-ssl-cert/days
+Type: string
+_Default: 30
+_Description: Lifetime of Certificate in Days
+ How many days should this certificate be valid for.
diff -irbwu ssl-cert-1.0.14/make-ssl-cert ssl-cert-1.0.14.0.olivier.0/make-ssl-cert
--- ssl-cert-1.0.14/make-ssl-cert       2006-05-18 14:02:20.000000000 +0200
+++ ssl-cert-1.0.14.0.olivier.0/make-ssl-cert   2007-02-15 11:49:47.000000000 +0100
@@ -9,7 +9,7 @@
 ask_via_debconf() {
     db_settitle make-ssl-cert/title
 
-    templates="countryname statename localityname organisationname ouname hostname email"
+    templates="countryname statename localityname organisationname ouname hostname email days"
 
     for i in $templates; do
        RET=""
@@ -48,6 +48,11 @@
      db_get make-ssl-cert/email
      Email="$RET"
      db_fset make-ssl-cert/email seen false
+
+     db_get make-ssl-cert/days
+     Days="$RET"
+     db_fset make-ssl-cert/days seen false
+
 }
 
 make_snakeoil() {
@@ -115,7 +120,7 @@
 export RANDFILE=/dev/random
 
 if [ "$1" != "generate-default-snakeoil" ]; then
-    openssl req -config $TMPFILE -new -x509 -nodes -out $output -keyout $output > /dev/null 2>&1
+    openssl req -config $TMPFILE -new -x509 -days $Days -nodes -out $output -keyout $output > /dev/null 2>&1
     chmod 600 $output
     # hash symlink
     cd $(dirname $output)
```

---

### Post by fortran01 on 2008-01-31
Find these lines: (Line 118, I think)

```
if [ "$1" != "generate-default-snakeoil" ]; then
    openssl req -config $TMPFILE -new -x509 -days 365 -nodes -out $output -keyout $output > /dev/null 2>&1
```

Replaces with:

```
if [ "$1" != "generate-default-snakeoil" ]; then
    openssl req -config $TMPFILE -new -x509 -days 365 -nodes -out $output -keyout $output > /dev/null 2>&1
```

or specify desired cert lifetime in days.

Yes, this is an Optional step.

---

### Post by techno-wiz on 2008-02-08
I'm using apache for accessing Nagios and trying to configure it to use SSL. I followed the howto posted here but when I try to restart apache I'm getting the following error.

(Command used) /etc/init.d/apache2 reload

Response:

open: Permission denied
* Reloading web server config apache2
5344
httpd not running, trying to start
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied



Not sure but it looks like maybe it is trying to use httpd.conf? If so that file is empty. My nagios.conf file is in the /etc/apache2/conf.d directory.

---

### Post by fortran01 on 2008-02-08
You are trying to start Apache as non-privileged?

---

### Post by techno-wiz on 2008-02-08
Sorry I was actually doing sudo before that command but still getting the same results.

I have made a bit of progress. I used the command force-reload instead of just reload and that did the trick. However now my nagios page cannot be displayed by either http or https!

I think I may have somehow in this process changed where apache is looking for its directories. Truth is I know nothing about apache and just got it working in the first place using the nagios quickstart guide. But I know my nagios.conf is under /etc/apache2/conf.d and when I look in my /etc/apache2/sites-available/ssl or /default they seem to be pointing to /var/www which for me only has apache2-default. Maybe I need to move the nagios.conf to /var/www ?

---

### Post by techno-wiz on 2008-02-08
Neither port 80 or 443 is open on the server after restarting apache2.

---

### Post by pneaveill on 2008-02-20
Want to add my thanks on this as well. Now to secure the folder from prying eyes . . . 

Ideas?

---

### Post by papayiya on 2008-03-16
> **jBilbo said:**
> :-s The above post is for apache1.

A Mini-Howto for apache2: :)

```
apt-get install apache2
apache2-ssl-certificate
```
(and answer the questions)

Now, enable ssl:
```
a2enmod ssl
```

configure ssl:
```
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/ssl
ln -s /etc/apache2/sites-available/ssl /etc/apache2/sites-enabled/ssl 
```
"/etc/apache2/sites-enabled/ssl"  should look like this:

```
NameVirtualHost *:443
<VirtualHost *:443>
(... configure the directories too...)
```
and "/etc/apache2/sites-enabled/default" should look like this:

```
NameVirtualHost *:80
<VirtualHost *:80>
(... configure the directories too...)
```
In /etc/apache2/ports.conf, add Listen 443

In the middle of /etc/apache2/sites-available/ssl file, insert this two lines:

```
SSLEngine On
SSLCertificateFile /etc/apache2/ssl/apache.pem
```

Hope it helps :)

Thanks for this.  Also be sure to open port 443 in your router!

---

