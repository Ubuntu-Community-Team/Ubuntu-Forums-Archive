---
title: "SSL Certificate not working after update 12.04.1lts to 12.10"
date: 2012-11-18
forum: General Help
---

### Post by ocpistol on 2012-11-18
getting errors, the main pages still work but the https:// are not working getting 
Website error 
[INDENT]SSL connection error
Unable to make a secure connection to the server. This may be a problem with the server, or it may be requiring a client authentication certificate that you don't have.
Error 107 (net::ERR_SSL_PROTOCOL_ERROR): SSL protocol error.[/INDENT]


errors starting apache2
[INDENT] ... waiting [Sun Nov 18 13:25:08 2012] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Nov 18 13:25:08 2012] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Nov 18 13:25:08 2012] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Nov 18 13:25:08 2012] [error] VirtualHost _default_:443 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Nov 18 13:25:08 2012] [error] VirtualHost *:443 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Nov 18 13:25:08 2012] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Nov 18 13:25:08 2012] [warn] NameVirtualHost *:0 has no VirtualHosts
[/INDENT]

---

### Post by ocpistol on 2012-11-18
Solved the problem 

Changed /etc/apache2/site-enabled to this 

[INDENT]<VirtualHost *>
        ServerAdmin .*.com
        ServerName .*.com
        DocumentRoot /home/user/.*.com/htdocs

</VirtualHost>

<IfModule mod_ssl.c>
<VirtualHost Server_IP:443>

        ServerAdmin .*.com
        ServerName .*.com
        DocumentRoot /home/user/.*.com/htdocs

        #   SSL Engine Switch:
        #   Enable/Disable SSL for this virtual host.
       SSLEngine on
        SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
    SSLCertificateFile /etc/ssl/certs/.*.com.crt
    SSLCertificateKeyFile /etc/ssl/private/.*.com.key
    SSLCertificateChainFile /etc/ssl/certs/.*.com.crt
</VirtualHost>

</IfModule>[/INDENT]

---

