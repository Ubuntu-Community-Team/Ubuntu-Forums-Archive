---
title: "Implementing SSL"
date: 2014-06-05
forum: General Help
---

### Post by rick29 on 2014-06-05
I have followed the tutorial for implementing SSL for my website and while it appears to be working, when I query the site on my local network it reports that the website is not encrypted and there is no lock symbol next to the URL.  Could this a problem with the virtualhost settings and assuming that it is could you post an example of a VirtualHost script that can handle two websites on the same server: mySite and Cloud using a self-signed CA.  Any other comments and suggestions would be welcomed.

---

### Post by TheFu on 2014-06-05
Uh ... which web server?
Any reverse proxy?
Did you close port 80 and open port 443?

Oh ... and running 2 HTTPS sites under the same IP is non-trivial. It requires many, many, many manual steps to get GnuTLS working.  
Also ... if you can post the exact commands used, that might be helpful. The history should have them.

I'm guessing this old how-to [http://www.howtoforge.com/hosting-multiple-ssl-web-sites-on-one-ip-address-with-apache-2.2-and-gnutls-debian-lenny](http://www.howtoforge.com/hosting-multiple-ssl-web-sites-on-one-ip-address-with-apache-2.2-and-gnutls-debian-lenny) is the best option for what you were trying?  I've not used it and it is a little old.  I don't believe that openssl supports name-based SSL.

[http://serverfault.com/questions/350127/how-to-setup-apache-namevirtualhost-on-ssl](http://serverfault.com/questions/350127/how-to-setup-apache-namevirtualhost-on-ssl) is another discussion about this.

It would be easier to setup 1 base website and use redirection subdirs for the alternate SSL websites .... or add multiple IPs on the webhost and listen for each different SSL on a different IP.

---

### Post by rick29 on 2014-06-05
The easy answers and solutions first.  I am using the latest versions of apache, mysql, PHP.  There is no reverse proxy.  I did not close port 80 but I did open port 443.  So let me start with one website only and I presume that I must close port 80 (I have several servers running on that port).  Is this the case?

---

### Post by TheFu on 2014-06-05
No - you can have 1, 50, 300 websites on port 80.  Name-based virtualhosting "just works" for non-encrypted connections, HTTP. This can happen on the same web server as the HTTPS connection too, but with 1 HTTPS website.  Having multiple name-based HTTPS websites needs much more help - I've never done it.

It is when SSL (HTTPS) is added that security and IP address complexities get into the way.  For a very long time (in internet time), 1 IP equaled 1 HTTPS website.  Did you review those links?

---

### Post by rick29 on 2014-06-05
I did review the links and in time I might even understand what I was reading.  I have a dynamic IP address and so I am using a name based solution.  I have attached the code:> 
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
    ServerAdmin [email]webmaster@mysite.ca[/email]
    ServerName gen.mysite.ca:443

    DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
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

    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

    #   SSL Engine Switch:
    #   Enable/Disable SSL for this virtual host.
    SSLEngine on

    #   A self-signed (snakeoil) certificate can be created by installing
    #   the ssl-cert package. See
    #   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
    #   If both key and certificate are stored in the same file, only the
    #   SSLCertificateFile directive is needed.
    SSLCertificateFile    /etc/apache2/ssl/apache.crt
    SSLCertificateKeyFile /etc/apache2/ssl/apache.key

    #   Server Certificate Chain:
    #   Point SSLCertificateChainFile at a file containing the
    #   concatenation of PEM encoded CA certificates which form the
    #   certificate chain for the server certificate. Alternatively
    #   the referenced file can be the same as SSLCertificateFile
    #   when the CA certificates are directly appended to the server
    #   certificate for convinience.
    #SSLCertificateChainFile /etc/apache2/ssl.crt/server-ca.crt

    #   Certificate Authority (CA):
    #   Set the CA certificate verification path where to find CA
    #   certificates for client authentication or alternatively one
    #   huge file containing all of them (file must be PEM encoded)
    #   Note: Inside SSLCACertificatePath you need hash symlinks
    #         to point to the certificate files. Use the provided
    #         Makefile to update the hash symlinks after changes.
    #SSLCACertificatePath /etc/ssl/certs/
    #SSLCACertificateFile /etc/apache2/ssl.crt/ca-bundle.crt

    #   Certificate Revocation Lists (CRL):
    #   Set the CA revocation path where to find CA CRLs for client
    #   authentication or alternatively one huge file containing all
    #   of them (file must be PEM encoded)
    #   Note: Inside SSLCARevocationPath you need hash symlinks
    #         to point to the certificate files. Use the provided
    #         Makefile to update the hash symlinks after changes.
    #SSLCARevocationPath /etc/apache2/ssl.crl/
    #SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl

    #   Client Authentication (Type):
    #   Client certificate verification type and depth.  Types are
    #   none, optional, require and optional_no_ca.  Depth is a
    #   number which specifies how deeply to verify the certificate
    #   issuer chain before deciding the certificate is not valid.
    #SSLVerifyClient require
    #SSLVerifyDepth  10

    #   Access Control:
    #   With SSLRequire you can do per-directory access control based
    #   on arbitrary complex boolean expressions containing server
    #   variable checks and other lookup directives.  The syntax is a
    #   mixture between C and Perl.  See the mod_ssl documentation
    #   for more details.
    #<Location />
    #SSLRequire (    %{SSL_CIPHER} !~ m/^(EXP|NULL)/ \
    #            and %{SSL_CLIENT_S_DN_O} eq "Snake Oil, Ltd." \
    #            and %{SSL_CLIENT_S_DN_OU} in {"Staff", "CA", "Dev"} \
    #            and %{TIME_WDAY} >= 1 and %{TIME_WDAY} <= 5 \
    #            and %{TIME_HOUR} >= 8 and %{TIME_HOUR} <= 20       ) \
    #           or %{REMOTE_ADDR} =~ m/^192\.76\.162\.[0-9]+$/
    #</Location>

    #   SSL Engine Options:
    #   Set various options for the SSL engine.
    #   o FakeBasicAuth:
    #     Translate the client X.509 into a Basic Authorisation.  This means that
    #     the standard Auth/DBMAuth methods can be used for access control.  The
    #     user name is the `one line' version of the client's X.509 certificate.
    #     Note that no password is obtained from the user. Every entry in the user
    #     file needs this password: `xxj31ZMTZzkVA'.
    #   o ExportCertData:
    #     This exports two additional environment variables: SSL_CLIENT_CERT and
    #     SSL_SERVER_CERT. These contain the PEM-encoded certificates of the
    #     server (always existing) and the client (only existing when client
    #     authentication is used). This can be used to import the certificates
    #     into CGI scripts.
    #   o StdEnvVars:
    #     This exports the standard SSL/TLS related `SSL_*' environment variables.
    #     Per default this exportation is switched off for performance reasons,
    #     because the extraction step is an expensive operation and is usually
    #     useless for serving static content. So one usually enables the
    #     exportation for CGI and SSI requests only.
    #   o StrictRequire:
    #     This denies access when "SSLRequireSSL" or "SSLRequire" applied even
    #     under a "Satisfy any" situation, i.e. when it applies access is denied
    #     and no other module can change it.
    #   o OptRenegotiate:
    #     This enables optimized SSL connection renegotiation handling when SSL
    #     directives are used in per-directory context.
    #SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
    <FilesMatch "\.(cgi|shtml|phtml|php)$">
        SSLOptions +StdEnvVars
    </FilesMatch>
    <Directory /usr/lib/cgi-bin>
        SSLOptions +StdEnvVars
    </Directory>

    #   SSL Protocol Adjustments:
    #   The safe and default but still SSL/TLS standard compliant shutdown
    #   approach is that mod_ssl sends the close notify alert but doesn't wait for
    #   the close notify alert from client. When you need a different shutdown
    #   approach you can use one of the following variables:
    #   o ssl-unclean-shutdown:
    #     This forces an unclean shutdown when the connection is closed, i.e. no
    #     SSL close notify alert is send or allowed to received.  This violates
    #     the SSL/TLS standard but is needed for some brain-dead browsers. Use
    #     this when you receive I/O errors because of the standard approach where
    #     mod_ssl sends the close notify alert.
    #   o ssl-accurate-shutdown:
    #     This forces an accurate shutdown when the connection is closed, i.e. a
    #     SSL close notify alert is send and mod_ssl waits for the close notify
    #     alert of the client. This is 100% SSL/TLS standard compliant, but in
    #     practice often causes hanging connections with brain-dead browsers. Use
    #     this only for browsers where you know that their SSL implementation
    #     works correctly.
    #   Notice: Most problems of broken clients are also related to the HTTP
    #   keep-alive facility, so you usually additionally want to disable
    #   keep-alive for those clients, too. Use variable "nokeepalive" for this.
    #   Similarly, one has to force some clients to use HTTP/1.0 to workaround
    #   their broken HTTP/1.1 implementation. Use variables "downgrade-1.0" and
    #   "force-response-1.0" for this.
    BrowserMatch "MSIE [2-6]" \
        nokeepalive ssl-unclean-shutdown \
        downgrade-1.0 force-response-1.0
    # MSIE 7 and newer should be able to use keepalive
    BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

</VirtualHost>
</IfModule>



---

### Post by TheFu on 2014-06-06
dbl post error

---

### Post by TheFu on 2014-06-06
Did you setup GnuTLS for Apache?  [https://wiki.apache.org/httpd/NameBasedSSLVHosts](https://wiki.apache.org/httpd/NameBasedSSLVHosts)
I think that is required if there is any hope of this working.

---

### Post by CharlesA on 2014-06-06
> **TheFu said:**
> No - you can have 1, 50, 300 websites on port 80.  Name-based virtualhosting "just works" for non-encrypted connections, HTTP. This can happen on the same web server as the HTTPS connection too, but with 1 HTTPS website.  Having multiple name-based HTTPS websites needs much more help - I've never done it.

It is when SSL (HTTPS) is added that security and IP address complexities get into the way.  For a very long time (in internet time), 1 IP equaled 1 HTTPS website.  Did you review those links?

Indeed. Some things support SNI - Server Name Indication so you can run multiple sites off the same IP, but not all services support it (dovecot doesn't). Apache and Nginx does though.

> **TheFu said:**
> Did you setup GnuTLS for Apache?  [https://wiki.apache.org/httpd/NameBasedSSLVHosts](https://wiki.apache.org/httpd/NameBasedSSLVHosts)
I think that is required if there is any hope of this working.

SSL should "just work" with apache as long as you have the module loaded. I use Nginx for the most part,

[https://help.ubuntu.com/14.04/serverguide/httpd.html](https://help.ubuntu.com/14.04/serverguide/httpd.html)

---

### Post by TheFu on 2014-06-06
CharlesA - do you use multiple name-based SSL for different websites and that "just works" on the same server with 1 IP?

---

### Post by CharlesA on 2014-06-06
> **TheFu said:**
> CharlesA - do you use multiple name-based SSL for different websites and that "just works" on the same server with 1 IP?

It should work as long as the browser supports SNI, otherwise you will need to have each site on their own IP address.

I use Nginx and host each SSL site on it's own IP after fighting with some services other than the web server.

---

### Post by TheFu on 2014-06-07
I've been using nginx for years - it is mainly a reverse proxy here to share 1 IP with a number of different backend web-apps.  Nginx rocks - COMPLETELY!

Only one is SSL, the others are virtual-names and not encrypted. These are a mix of name-based domains and sub-directories (not really relevant here).   After loading a few 5 yr commercial SSL certs 2-3 months ago, I'm tempted to install others. It was easy, but I knew that for years, having more than 1 HTTPS website on a single IP was an issue where client support was needed.  

It has been long enough that most popular client browsers probably support SNI now - though I can't say if any smartphone browsers do.  I doubt that lynx (all versions used here) do.  The lynx change log does show they added SNI support, but not until 13.xx releases at the earliest.  
[https://en.wikipedia.org/wiki/Server_Name_Indication#Support](https://en.wikipedia.org/wiki/Server_Name_Indication#Support) says that support is really wide-spread and should "just work" most of the time.  Looks like I'm out of the loop ... again. ;(

---

### Post by CharlesA on 2014-06-07
It happens, even if you keep up-to-date with stuff. :)

You can test browsers (and servers!) with the tool here: [https://www.ssllabs.com/](https://www.ssllabs.com/)

---

### Post by rick29 on 2014-06-09
Sorry for the hiatus but other tasks called.  I am trying to implement the gnuTLS module and before I complete the process I need an answer to the following process.  The NameVirtualHost IP address - is this the IP address on the local host 127.0.0.1 or the IP address of the machine hosting the site: 192.168.1.3 or the IP address assigned by the service provider that equates to the domain name: xx.yy.zz.kk.  I presume it is the later since that is what the the world sees.  But, because my website IP address is dynamic this will change as the ISP decides to change it.  So can I use the domain name in its place for the various different domains on the same IP address: eg - site1.mysite.com, site2.mysite.com, etc.  An actual example would be helpful and sorry for my lack of knowledge in this area.

---

### Post by CharlesA on 2014-06-09
If you have a dynamic IP address, you would need some form of Dynamic DNS to ensure your site stays online even if your IP address changes.

---

### Post by rick29 on 2014-06-10
I do have DDNS installed.  So the question remains, which IP address do I use and can I use name based with gnuTLS?

---

### Post by CharlesA on 2014-06-10
You should be able to.. I'm confused though, I thought Apache used OpenSSL by default, not gnuTLS? Where did you find out it used gnuTLS?

---

