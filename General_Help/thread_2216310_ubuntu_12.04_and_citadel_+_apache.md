---
title: "ubuntu 12.04 and citadel + apache"
date: 2014-04-11
forum: General Help
---

### Post by Alexandre_Jaquet on 2014-04-11
Hi,

I've my web application configured on my localhost machine and I just installed citadel, I could not anymore connect to my webapp trough the port 80, it's redirect me to the citadel page.

Here is my configuration of my site avaiable 

<code>


<VirtualHost *:80>
  ServerAdmin [EMAIL="alexjaquet@gmail.com"]alexjaquet@gmail.com[/EMAIL]
  ServerName  [www.avant-garde.no-ip.biz]("http://www.avant-garde.no-ip.biz")
  ServerAlias avant-garde.no-ip.biz
  DirectoryIndex index.html
  DocumentRoot /home/alexandre/apache/site/recordz1/
    <Directory /home/apache/recordz/apaches/site/recordz/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
    </Directory>

        ScriptAlias /cgi-bin/ /home/alexandre/apache/cgi-bin/
    <Directory /home/alexandre/apache/cgi-bin/>
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
   ErrorLog ${APACHE_LOG_DIR}/error.log
   LogLevel warn
   CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
<VirtualHost *:443>
      ServerName  [www.avant-garde.no-ip.biz]("http://www.avant-garde.no-ip.biz")
      ServerAlias avant-garde.no-ip.biz
      DocumentRoot /home/alexandre/apache/site/recordz1/
       <Directory /home/apache/recordz/apaches/site/recordz/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
      </Directory>
        ScriptAlias /cgi-bin/ /home/alexandre/apache/cgi-bin/
    <Directory /home/alexandre/apache/cgi-bin/>
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
        SSLEngine on
        SSLCertificateFile /etc/apache2/server.crt
    SSLCertificateKeyFile /etc/apache2/server.key
        LogLevel warn
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

and the config file for citadel webcit.conf

<code>
# if you want to have this in just one virtual host
# context, remove the symbolic link from /etc/apachenn/conf.d
# and rather do something like
 <virtualhost avant-garde.no-ip.biz>
   Servername avant-garde.no-ip.biz:2000
   include /etc/citadel/webcit.conf
 </virtualhost>

<location /webcit>
        Allow from all
</location>
<location /listsub>
        Allow from all
</location>
<location /groupdav>
        Allow from all
</location>

ProxyPass /webcit/ [http://127.0.0.1:8504/webcit/](http://127.0.0.1:8504/webcit/)
ProxyPassReverse /webcit/ [http://127.0.0.1:8504/webcit/](http://127.0.0.1:8504/webcit/)

ProxyPass /listsub [http://127.0.0.1:8504/listsub](http://127.0.0.1:8504/listsub)
ProxyPassReverse /listsub [http://127.0.0.1:8504/listsub](http://127.0.0.1:8504/listsub)

ProxyPass /groupdav/ [http://127.0.0.1:8504/groupdav/](http://127.0.0.1:8504/groupdav/)
ProxyPassReverse /groupdav/ [http://127.0.0.1:8504/groupdav/](http://127.0.0.1:8504/groupdav/)

ProxyPass /who_inner_html [http://127.0.0.1:8504/who_inner_html](http://127.0.0.1:8504/who_inner_html)
ProxyPassReverse /who_inner_html [http://127.0.0.1:8504/who_inner_html](http://127.0.0.1:8504/who_inner_html)

alias /static /usr/share/citadel-webcit/static
alias /tiny_mce /usr/share/tinymce/www


</code>


how can I tell citadel to use another port than 80 ?

Thanks

Alexandre

---

