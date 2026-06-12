---
title: "Site Redirects to Subdomain if &quot;www.&quot; is not typed in URL"
date: 2023-12-14
forum: General Help
---

### Post by rmcg3 on 2023-12-14
Hi,
I am running a WordPress site on Ubuntu 20.04.5 LTS (GNU/Linux 5.16.11-051611-generic x86_64), we'll call it myDomain.com.

I have a .NET Core app  deployed on the same server with the domain name like: myApp.myDomain.com.

If you do not have [www.myDomain.com](www.myDomain.com) cached in your browser and you type in the address bar "myDomain.com", you get redirected to myApp.myDomain.com instead of [www.myDomain.com](www.myDomain.com).

I have made a ton of changes to the .htaccess file in WordPress and it did not fix the issue so I am thinking that it's my Apache .conf file for my .NET application:

```
<VirtualHost *:*>
    RequestHeader set "X-Forwarded-Proto" expr=%{REQUEST_SCHEME}
</VirtualHost>


<VirtualHost *:80>
    ProxyPreserveHost On


    ProxyPass / http://myDomainIP:5003/
    ProxyPassReverse / http://myDomainIP:5003/
    ServerName myApp.myDomain.com
    ServerAlias *.myApp.myDomain.com


    ErrorLog ${APACHE_LOG_DIR}myApp-error.log
    CustomLog ${APACHE_LOG_DIR}myApp-access.log common
</VirtualHost>


<VirtualHost *:443>


    ServerName myApp.myDomain.com


    # Header always set Content-Security-Policy "script-src 'self' 'unsafe-inline'"


    Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains"
    SSLEngine on
    SSLCertificateFile /etc/ssl/crt/myCert.crt
    SSLCertificateKeyFile /etc/ssl/crt/myWildcardCert.key
    SSLCertificateChainFile /etc/ssl/crt/myCertFile.crt
    ErrorLog ${APACHE_LOG_DIR}httpsmyApp-error.log
    CustomLog ${APACHE_LOG_DIR}httpsmyApp-access.log common


    ProxyPreserveHost On


    ProxyPass / http://myDomainIP:5003/
    ProxyPassReverse / http://myDomainIP:5003/
</VirtualHost>



```

Any thoughts on if this could be why this redirection happens?

Thanks in advance

---

### Post by dragonfly41 on 2023-12-14
A hunch only .. possible red herring .. but have you studied how to setup /etc/hosts? I vaguely remember a similar issue.

---

### Post by rmcg3 on 2023-12-14
I have not looked into this as I am not using it. Thank you for your reply

---

### Post by SeijiSensei on 2023-12-15
Where is the VirtualHost definition for [noparse]www.mydomain.com[/noparse]?
```

ServerName     www.mydomain.com
ServerAlias       mydomain.com
DocumentRoot /path/to/your/wordpress/site

```
so that queries for either of those names are handled by WordPress.

Your DNS server also has to be configured correctly if you are using one.

---

### Post by rmcg3 on 2023-12-17
here is the VirtualHost definition for [www.myDomain.com:](www.myDomain.com:)

```
<VirtualHost *:80>
ServerAdmin webmaster@localhost
ServerName myDomain.com
ServerAlias www.myDomain.com
Redirect / https://www.myDomain.com/
DocumentRoot /var/www/html
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains; preload"
</VirtualHost>


<VirtualHost *:443>
DocumentRoot /var/www/html
ServerName www.myDomain.com


# Header always set Content-Security-Policy "script-src 'self' 'unsafe-inline'"


Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains"
SSLEngine on

SSLCertificateFile /etc/ssl/crt/myCert.crt
SSLCertificateKeyFile /etc/ssl/crt/myWildcardCert.key
SSLCertificateChainFile /etc/ssl/crt/myCertFile.crt
</VirtualHost>
```

---

### Post by SeijiSensei on 2023-12-18
Is mydomain.com on the public Internet? What if you run
```
host www.mydomain.com
host mydomain.com

```
Do they both point to the same server?

---

### Post by SeijiSensei on 2023-12-18
> **rmcg3 said:**
> here is the VirtualHost definition for [www.myDomain.com:](www.myDomain.com:)

```
<VirtualHost *:80>
ServerAdmin webmaster@localhost
ServerName myDomain.com
ServerAlias www.myDomain.com
Redirect / https://www.myDomain.com/
DocumentRoot /var/www/html
ErrorLog ${APACHE_LOG_DIR}/error.log
CustomLog ${APACHE_LOG_DIR}/access.log combined
Header always set Strict-Transport-Security "max-age=63072000; includeSubDomains; preload"
</VirtualHost>


<VirtualHost *:443>
DocumentRoot /var/www/html
ServerName www.myDomain.com
**ServerAlias myDomain.com**
</VirtualHost>
```

You need a ServerAlias in the HTTPS definition as well. You redirect port 80 traffic to port 443, but the listener on that port doesn't have a matching virtual host name.

I think everything below the Redirect line in the first stanza is ignored since the request will have already been redirected. I include all the items like DocumentRoot, logging, etc, in the HTTPS stanza.

```
<VirtualHost    *:80>
ServerName      something.org
ServerAlias     www.something.org
Redirect permanent / https://something.org/
</VirtualHost>


<VirtualHost    *:443>
DocumentRoot    /path/to/website/files
ServerName      something.org
ServerAlias www.something.org
ErrorLog        logs/error_log-something_org_errors
[etc.]
</VirtualHost

```

---

### Post by rmcg3 on 2023-12-19
yes myDomain.com is on the public internet
Found something with this.

[www.myDomain.com:]("http://www.myDomain.com:")
```

host www.myDomain.com
www.myDomain.com has address 172.XX.XX.**XX6**

```

myDomain.com
```

host myDomain.com
myDomain.com has address 172.XX.XX.**X9  **(a domain controller)

myDomain.com has address 10.XX.X.XX  (correct DNS )
myDomain.com has address 10.XX.X.XX
myDomain.com has address 10.XX.X.XX
myDomain.com has address 10.XX.X.XX




```

---

### Post by rmcg3 on 2023-12-19
Ok I understand, this makes sense.
Thank you for this I will try it.

---

### Post by SeijiSensei on 2023-12-21
If that fixed your problem, please go to Thread Tools at the top of this page and mark the thread SOLVED.

---

