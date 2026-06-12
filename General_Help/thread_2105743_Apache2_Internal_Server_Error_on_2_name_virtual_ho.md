---
title: "Apache2 Internal Server Error on 2 name virtual host websites"
date: 2013-01-16
forum: General Help
---

### Post by hockeymikey on 2013-01-16
Hello I am new to Ubuntu forums after lurking for awhile I have been faced with a problem that I can't search for a solution for.  I have 4 websites on my small apache webserver on Ubuntu 12.04.  2 of these websites work fine while the other 2 do not.  When I try to go to either one of the two they give me a page with 
```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, hockeymikey@live.com and inform them them the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
```

So I checked the logs I got this.
```

[Wed Jan 16 21:09:01 2013] [error] [client 69.31.69.111] Request exceeded the limit of 10 internal redirects due to probable configuration error. Use 'LimitInternalRecursion' to increase the limit if necessary. Use 'LogLevel debug' to get a backtrace.

```

I then used loglevel debug and looked in the rewrite.log got this
```

69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b756ecc8/initial/redir#9] (3) [perdir /var/www/] applying pattern '(.*)' to uri 'croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/'
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b756ecc8/initial/redir#9] (2) [perdir /var/www/] rewrite 'croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/' -> 'app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/'
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b756ecc8/initial/redir#9] (3) [perdir /var/www/] add per-dir prefix: app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/ -> /var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b756ecc8/initial/redir#9] (1) [perdir /var/www/] internal redirect with /var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/ [INTERNAL REDIRECT]
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (3) [perdir /var/www/] add path info postfix: /var/www/croxcrew/var -> /var/www/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (3) [perdir /var/www/] strip per-dir prefix: /var/www/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/ -> croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (3) [perdir /var/www/] applying pattern '^$' to uri 'croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/'
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (3) [perdir /var/www/] add path info postfix: /var/www/croxcrew/var -> /var/www/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (3) [perdir /var/www/] strip per-dir prefix: /var/www/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/ -> croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (3) [perdir /var/www/] applying pattern '(.*)' to uri 'croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/'
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (2) [perdir /var/www/] rewrite 'croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/' -> 'app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/'
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (3) [perdir /var/www/] add per-dir prefix: app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/ -> /var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/
69.31.69.111 - - [16/Jan/2013:20:14:10 --0600] [croxcrew.com/sid#b7754518][rid#b753e4c8/initial/redir#10] (1) [perdir /var/www/] internal redirect with /var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/var/www/app/webroot/croxcrew/ [INTERNAL REDIRECT]


```

The other site Minecraftr.us gives out about the same thing.
I have read about the .htacess has a mistake but both croxcrew (non working) and aqmc (working) both are using Xenforo and .htaccess files are the same.
```
#    Mod_security can interfere with uploading of content such as attachments. If you
#    cannot attach files, remove the "#" from the lines below.
#<IfModule mod_security.c>
#    SecFilterEngine Off
#    SecFilterScanPOST Off
#</IfModule>

ErrorDocument 401 default
ErrorDocument 403 default
ErrorDocument 404 default
ErrorDocument 500 default

<IfModule mod_rewrite.c>
    RewriteEngine On

    #    If you are having problems with the rewrite rules, remove the "#" from the
    #    line that begins "RewriteBase" below. You will also have to change the path
    #    of the rewrite to reflect the path to your XenForo installation.
    #RewriteBase /xenforo

    #    This line may be needed to enable WebDAV editing with PHP as a CGI.
    #RewriteRule .* - [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

    RewriteCond %{REQUEST_FILENAME} -f [OR]
    RewriteCond %{REQUEST_FILENAME} -l [OR]
    RewriteCond %{REQUEST_FILENAME} -d
    RewriteRule ^.*$ - [NC,L]
    RewriteRule ^(data/|js/|styles/|install/|favicon\.ico|crossdomain\.xml|robots\.txt) - [NC,L]
    RewriteRule ^.*$ index.php [NC,L]
</IfModule>
```
So this shouldn't be the problem, so what is?

I'm not the most experienced at linux as I have only been using it for about 2 months "well".

Thanks

---

### Post by hockeymikey on 2013-01-17
Please does anyone have an answer? I need this for school tomorrow.

---

