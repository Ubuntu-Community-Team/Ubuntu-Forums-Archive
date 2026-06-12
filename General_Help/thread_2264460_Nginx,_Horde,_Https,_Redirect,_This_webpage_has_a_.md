---
title: "Nginx, Horde, Https, Redirect, This webpage has a redirect loop"
date: 2015-02-07
forum: General Help
---

### Post by axetone on 2015-02-07
I have an NGINX server with Horde installed so I can use webmail, and am getting two different errors depending on whether I'm using http -or- httpS.
I have setup debug within nginx and am not getting any inclination as to what the source of the error is.
Mail error/access logs have no errors.
I have successfully setup Postfix, and Dovecot (both tested/connected from telnet and Open_ssl from CLI).
 My IP-ports are open (as needed).

Http works fine ([http://www.mydomain.com/index.php](http://www.mydomain.com/index.php)).
Http_**S**_ does _NOT_ work with this same URL.

Http_**S**_ does load the _**webmail**_ loginPage BUT...
   1. The page doesn't look right. It looks nothing like what it did when I was using Apache2 which leads me to believe something is not processing PHP correctly.
   2. I cannot login directly through this _**webmail**_ login page, BUT I can login using the _**Horde-TEST.php**_ page provided by Horde.
         Note:  _**webmail**_         [http://www.mydomain.com/webmail/](http://www.mydomain.com/webmail/)_**login.php**_
                   _**Horde-Test**_     [http://www.mydomain.com/webmail/](http://www.mydomain.com/webmail/)_**test.php**_

    So....
       A) regular loginPage (loads, but can't login)
           (http_**S**_://www.mydomain.com/**webmail**/login.php)

       B) Horde-Mail Test page ([http://www.mydomain.com/webmail/](http://www.mydomain.com/webmail/)_**test.php**_) also does load and the test(s) login is working for all imap/imapS and pop3/pop3S in the browser. PLEASE KEEP IN MIND THAT THIS LOGIN PAGE IS NOT THE SAME AS THE WEBMAIL LOGIN PAGE!

           -however, the test login page does not load at all if swtiched to httpS
               http_**S**_://www.mydomain.com/webmail/test.php

---

When I setup a redirect for http to force https, the **main** website page not load "httpS://www.mydomain.com/index.php", but the **webmail** login page still does load...-but as before it will not let me log in...keeps giving me "Error ERR_CONNECTION_TIMED_OUT". And finally, the **Horde-test.php** stops working when using forced http**S**.

Lastly, I have verified that my php5-fpm config file "/etc/php5/fpm/pool.d/www.conf" user/group statement (nginx) and the listen statement (listen = /tmp/php5-fpm.sock) are in agreement with what's setup in my nginx.conf configuration "fastcgi_pass unix:/tmp/php5-fpm.sock;".

 And I should mention, I also have prestashop loaded in the root website directory and there are no PHP errors with any of its functionality...-but I'm not suing any httpS on it at this time either...just http.

In summary:
I have errors when trying to use HTTPS.
1. http_**S**_ will _not_ load the main webpage.
2. http_**S**_ will load the Horde_test page., AND the test tools connects successfully to imap/imaps/pop3/pop3s.
3. http will load the webmail login page, but gives "Error ERR_CONNECTION_TIMED_OUT".

The only known error that I am getting is from the CLI after reloading nginx whenever I've made a change to nginx.conf (even if I just add a comment line and change nothing else!) this is what happens:
```

$ sudo service nginx reload
/etc/init.d/nginx: 2: /etc/init.d/nginx: Syntax error: newline unexpected

```

-and sadly, once this happens...even the regualr main page without httpS now gives "ERR_TOO_MANY_REDIRECTS"...only rebooting starts this http working again.

Here's my nginx.conf file.
```

user nginx;
worker_processes 4;
pid /var/run/nginx.pid;


events {
        worker_connections 768;
        # multi_accept on;
}


error_log /var/log/nginx/debuglog       debug;


http {


        ##
        # Basic Settings
        ##


        sendfile on;
        tcp_nopush on;
        tcp_nodelay on;
        keepalive_timeout 65;
        types_hash_max_size 2048;


        include /etc/nginx/mime.types;
        default_type application/octet-stream;


        access_log /var/log/nginx/access.log;
        error_log /var/log/nginx/error.log;




server {
        listen   80; ## listen for ipv4; this line is default and implied
        #listen   [::]:80 default ipv6only=on; ## listen for ipv6


        server_name mydomain.com *.mydomain.com;


        #Force http to use httpS
        #NOTE: I've turned this on ONLY to test...-same errors output for httpS noted in posting
        rewrite ^ https://$http_host$request_uri? permanent;    # force redirect http to https
                }






# HTTPS server
server {
        listen 443;
        keepalive_timeout   70;
        ssl_protocols       SSLv3 TLSv1 TLSv1.1 TLSv1.2;
        ssl_ciphers         AES128-SHA:AES256-SHA:RC4-SHA:DES-CBC3-SHA:RC4-MD5;
        ssl_prefer_server_ciphers on;
        ssl on;
        ssl_certificate /etc/nginx/ssl/server.crt;
        ssl_certificate_key /etc/nginx/ssl/server.key;
        server_name mydomain.com *.mydomain.com;
        
         #ssl_ciphers ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv3:+EXP;


   # pass the PHP scripts to FastCGI server
        location ~ \.php$ {
                fastcgi_split_path_info ^(.+?.php)(.*)$;
                if (!-f $document_root$fastcgi_script_name) {
                        return 404;
                        }
                #fastcgi_pass 127.0.0.1:9000;
                #fastcgi_pass unix:/var/run/php5-fpm.sock;
                fastcgi_pass unix:/tmp/php5-fpm.sock;
                fastcgi_index index.php;
                include fastcgi_params;
                        }


        root /usr/share/nginx/www/wcrc;
        index index.php index.html index.htm;


       }
}


# I'm not using the direct mail ports below as I'm using TLS through the browser/Horde-webmail instead.


#mail {
#       # See sample authentication script at:
#       # http://wiki.nginx.org/ImapAuthenticateWithApachePhpScript
#
#       # auth_http localhost/auth.php;
#       # pop3_capabilities "TOP" "USER";
#       # imap_capabilities "IMAP4rev1" "UIDPLUS";
#
#       server {
#               listen     localhost:110;
#               protocol   pop3;
#               proxy      on;
#       }
#
#       server {
#               listen     localhost:143;
#               protocol   imap;
#               proxy      on;
#       }
#}

```


PORTS OPEN:
$ sudo netstat -ntlp | grep LISTEN
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1744/nginx
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      938/dovecot
tcp        0      0 0.0.0.0:995             0.0.0.0:*               LISTEN      938/dovecot
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      985/mysqld
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN      938/dovecot
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      938/dovecot
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1744/nginx
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      831/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      800/sshd
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1215/master
tcp6       0      0 :::22                   :::*                    LISTEN      800/sshd

---

### Post by axetone on 2015-02-07
System got messed up when I installed another tool that also installed Apache. I found this by looking at the active ports.
I uninstalled Apache, and then to remove other variables I also de-configured httpS from nginx.
My php config was also a bit testy, so I streamlined that down to the bare minimun just to make sure that PHP was not the problem.
Non-httpS URL's will work if I type them exactly with /index.php, but regular default URL's do not work and give 403-forbidden error. (Permissions issue).

Lastly, to avoid any other complicaitons I'm also going to uninstall Prestashop. Don't need it, was just testing its speed with FastCgi -and it did perform well.
So, getting Horde to work with NGINX has not been a clean setup the first go around. I'm closing this as a Permissions mis-configuration coupled with a rogue install conflict with Apache.

---

