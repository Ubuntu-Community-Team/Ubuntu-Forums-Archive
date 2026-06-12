---
title: "sogo outlook connectoin issues"
date: 2014-02-15
forum: General Help
---

### Post by paul95 on 2014-02-15
[FONT=-moz-fixed]Hey guys and girls! 

I've been trying to install sogo with openchange for 3 weeks now, but  without luck so far. 
I hope that  someone could help me. 
A few words to my environment: 
I'm on a vbox with ubuntu 12.04.04 running on a windows server 2008 R2  Sp1 AD. 
what is running: 
samba joined to AD as a DC with bind9_DLZ - ok. repl is ok, fsmo schema  is transfered. we are not master but uptades are enabled 
openchange is provisioned, openchangedb is provisioned, users from the  samba user list are created within openchange. because I'm not sure if  we have trust between imap and openchange I created the passwrod files  in [I]/var/lib/samba/private/%username/password. 
dovecot with postfix is running over ldap. I can send and receive mails. 
sogo web with https on port 8843 and 443 with a startssl cert is  working. userauth runs also over ldap. -working 
Iphone, thunderbird connection to caldav, carddav and email is working best. 
The one thing which is not working is outlook. 
I can't connect to the server, although I have set  _autodiscover._tc.gw.myserver.com as SRV in my tcp table on the server,  a cname alias for autodiscover pointing to gw.myserver.com in my  domainISP DNS-Settings and a hosts entry for autodiscover on the  external address on the client. 
Port 135 is opened and listening. 
Openchange log only show similar entries, like that: 
 INFO  [openchange.web.auth.NTLMAuthHandler] [worker 7] client did not  pass auth cookie 
I suppose it's something within my apache conf, and/or the dns settings.  active sync isn't working also. When I'm trying to connect with active  sync outlook is showing that autodiscover.mydomain.com has a wrong name  for that certificate. (cert issue)The certificate i have is only for  mydomain.com and gw.mydomain.com (which is my mail,sogo-server), 
mydomain.com is the ad. 
Here is my default for apache sites enabled: 
<VirtualHost *:80> 
   Servername gw.mydomain.com 
   RedirectMatch permanent ^/ [https://gw.mydomain.com:8843/SOGo](https://gw.mydomain.com:8843/SOGo) 
   RedirectMatch permanent ^/SOGo [https://gw.mydomain.com:8843/SOGo](https://gw.mydomain.com:8843/SOGo) 
</VirtualHost> 

<VirtualHost *:8843> 
    Servername gw.mydomain.com 
ErrorLog /var/log/apache2/error.log 
    CustomLog /var/log/apache2/access.log combined 
    SSLEngine on 
SSLCertificateFile /etc/ssl/certs/ca_gw.crt 
SSLCertificateKeyFile /etc/ssl/private/gw.mydomain.com.key 
SSLCertificateChainFile /etc/ssl/certs/class1.pem 
SSLProtocol all -SSLv2 
SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM 
DocumentRoot [I]/usr/lib/GNUstep/SOGo/WebServerResources/ 
ProxyRequests Off 
SetEnv proxy-nokeepalive 1 
ProxyPreserveHost On 

ProxyPassInterpolateEnv On 
#for CalDAV 
ProxyPass /SOGo [http://127.0.0.1:20000/SOGo](http://127.0.0.1:20000/SOGo) interpolate 
ProxyPass [I]/proxy [http://127.0.0.1:20000/SOGo/dav/](http://127.0.0.1:20000/SOGo/dav/) interpolate 
#ProxyPass / [http://127.0.0.1:20000/SOGo/dav/](http://127.0.0.1:20000/SOGo/dav/) interpolate 

<Proxy ["http://127.0.0.1:20000/SOGo"]("http://127.0.0.1:20000/SOGo")> 
## adjust the following to your configuration 
  RequestHeader set "x-webobjects-server-port" "8843" 
  RequestHeader set "x-webobjects-server-name" "gw.mydomain.com:8843" 
  RequestHeader set "x-webobjects-server-url"  ["https://gw.mydomain.com:8843"]("https://gw.mydomain.com:8843") 
  RequestHeader set "x-webobjects-server-protocol" "HTTP/1.0" 
 RequestHeader set "x-webobjects-remote-host" "127.0.0.1" 
  RequestHeader set "x-webobjects-remote-host" %{REMOTE_HOST}e  env=REMOTE_HOST 
  AddDefaultCharset UTF-8 
  Order allow,deny 
  Allow from all 
</Proxy> 
RewriteEngine On 
RewriteRule ^[I]/SOGo/(.*)$ [I]/SOGo/$1 [env=REMOTE_HOST:%{REMOTE_ADDR},PT] 
RewriteRule ^[I]/principals/users/(.*)$ [I]/proxy/$1 [PT] 
Redirect permanent /index.html [https://gw.mydomain.com/SOGo](https://gw.mydomain.com/SOGo) 
</VirtualHost> 

<VirtualHost *:443> 
    Servername gw.mydomain.com 
ErrorLog /var/log/apache2/error.log 
    CustomLog /var/log/apache2/access.log combined 
    SSLEngine on 
SSLCertificateFile /etc/ssl/certs/ca_gw.crt 
SSLCertificateKeyFile /etc/ssl/private/gw.mydomain.com.key 
SSLCertificateChainFile /etc/ssl/certs/class1.pem 
SSLProtocol all -SSLv2 
SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM 
DocumentRoot [I]/usr/lib/GNUstep/SOGo/WebServerResources/ 
ProxyRequests Off 
SetEnv proxy-nokeepalive 1 
ProxyPreserveHost On 

ProxyPassInterpolateEnv On 
#for CalDAV 
ProxyPass /SOGo [http://127.0.0.1:20000/SOGo](http://127.0.0.1:20000/SOGo) interpolate 
ProxyPass [I]/proxy [http://127.0.0.1:20000/SOGo/dav/](http://127.0.0.1:20000/SOGo/dav/) interpolate 
ProxyPass / [http://127.0.0.1:20000/SOGo/dav/](http://127.0.0.1:20000/SOGo/dav/) interpolate 

<Proxy ["http://127.0.0.1:20000/SOGo"]("http://127.0.0.1:20000/SOGo")> 
## adjust the following to your configuration 
  RequestHeader set "x-webobjects-server-port" "443" 
  RequestHeader set "x-webobjects-server-name" "gw.mydomain.com:443" 
  RequestHeader set "x-webobjects-server-url" ["https://gw.mydomain.com:443"]("https://gw.mydomain.com:443") 
  RequestHeader set "x-webobjects-server-protocol" "HTTP/1.0" 
 # RequestHeader set "x-webobjects-remote-host" "127.0.0.1" 
  RequestHeader set "x-webobjects-remote-host" %{REMOTE_HOST}e  env=REMOTE_HOST 
  AddDefaultCharset UTF-8 
  Order allow,deny 
  Allow from all 
</Proxy> 
RewriteEngine On 
RewriteRule ^[I]/SOGo/(.*)$ [I]/SOGo/$1 [env=REMOTE_HOST:%{REMOTE_ADDR},PT] 
RewriteRule ^[I]/principals/users/(.*)$ [I]/proxy/$1 [PT] 
Redirect permanent /index.html [https://gw.mydomain.com/SOGo](https://gw.mydomain.com/SOGo) 
</VirtualHost> 
sogo.conf is uncahnged like the rest of the conf files in apaches conf.d  dir. 
  port 443 is for caldav and carddav for the iphone. port 8843 is only  for the web access, because of that line: 
ProxyPass / [http://127.0.0.1:20000/SOGo/dav/](http://127.0.0.1:20000/SOGo/dav/) interpolate which is like I  tested needed by the iphone but causing a blank site on the web site  which shows only  the username and password inputfields, css is not  working and a login is also not possible. 
when I create the profile in outlook like written outlook can  succesfully resolve the name. outlook is starting but keeps asking me  for the passowrd. Thats all. 
I hope that someone will try on that, because I can't get it working. 
Thanks a lot in advice. 
greets, 
Paul 
[/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/I][/FONT]

---

### Post by paul95 on 2014-02-15
ok, I'm a little bit further. I can now login with outlook, but no mails, calendars, or addressbook are being displayed. autodiscovery isn't working at all, and again outlook keeps asking me for a password and is after the first connection not connecting any more to the  server. ocsmanager.log displays the same info: [FONT=-moz-fixed][I]INFO  [openchange.web.auth.NTLMAuthHandler] client did not  pass auth cookie. And the rpc service crashes after some tries. samba needs then a restart. Oh and outlook keeps showing me the wrong certificate message.  
Oh yes: the versions: samba 4.0.1 and the latest sogo openchange (I think 2.1.1b)
Does someone have a hint?
Thanks a lot.

[/I][/FONT]

---

### Post by paul95 on 2014-02-15
update: installed new cert, outlook does not display the cert error anymore, the connection problems are still there. 
No one a hint?
Thanks.

---

### Post by paul95 on 2014-02-16
I'm not sure what to configure in apache or sogo.conf or the windows server in order to get it working. 
Somebody? A hint?

---

### Post by Allen_Shi on 2014-08-22
Hi paul95,

i'm currently have same problem with the one you had. How did you make it a little bit further?


> **paul95 said:**
> ok, I'm a little bit further. I can now login with outlook, but no mails, calendars, or addressbook are being displayed. autodiscovery isn't working at all, and again outlook keeps asking me for a password and is after the first connection not connecting any more to the  server. ocsmanager.log displays the same info: [FONT=-moz-fixed][I]INFO  [openchange.web.auth.NTLMAuthHandler] client did not  pass auth cookie. And the rpc service crashes after some tries. samba needs then a restart. Oh and outlook keeps showing me the wrong certificate message.  
Oh yes: the versions: samba 4.0.1 and the latest sogo openchange (I think 2.1.1b)
Does someone have a hint?
Thanks a lot.

[/I][/FONT]

---

### Post by oldos2er on 2014-08-22
paul95 hasn't visited the forums since February, so you're far more likely to get help if you create a new thread.

---

