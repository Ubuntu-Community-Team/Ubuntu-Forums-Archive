---
title: "Svn HTTPS and the 502 bad gateway error"
date: 2007-11-22
forum: General Help
---

### Post by Inuyaga on 2007-11-22
**The situation:**
SVN has been setup using svn_dav with ssl enabled

**default site file**
```
<VirtualHost ***.**.**.130:443>
        <Directory /var/www/>
                Options -Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        <IfModule mod_ssl.c>
                SSLEngine on
                SSLCipherSuite ALL:!ADH:!EXPORT56:RC4+RSA;+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
                SSLCertificateFile /var/ssl/crt/svn.crt
                SSLCertificateKeyFile /var/ssl/key/svn.key
        </IfModule>
</VirtualHost>
```

**svn.mysite file**
```
<VirtualHost ***.***.***.130:443>
        ServerName ***************
        ServerAdmin ***************

        DocumentRoot /var/www/null

        <Location "/">
                <IfModule mod_ssl.c>
                        SSLRequireSSL
                </IfModule>

                DAV svn
                SVNPath /var/svn/
                AuthType Basic
                AuthName "svn@********.***"
                AuthUserFile /var/svn/conf/dav.passwd
                AuthzSVNAccessFile /var/svn/conf/authz
                 Require valid-user

        </Location>

        ErrorLog /var/log/svn.error.log
        CustomLog /var/log/svn.access.log combined

</VirtualHost>
```

**NOTE there is also a file that describes mysite.com but I have not included that. The site names and alias do not overlap in any way and it specifically uses port 80. If this accly is the problem and apache can not handle having a site and the svn at the same time can someone please recommend a web server that can?

Sorry for the ***********'s but Id rather no post that info all over the place. ^_^

**The symptoms:**
Evey thing pretty much works. I can check out and commit and generally do most svn like things. However the COPY command DOES NOT work. It keeps giveing me a 502 bad gateway error.

**Background:**
Here are some things that I think may describe the error im havening.
[http://svn.haxx.se/users/archive-2006-03/0549.shtml](http://svn.haxx.se/users/archive-2006-03/0549.shtml)
[http://www.science.uva.nl/research/air/wiki/Subversion502BadGateway](http://www.science.uva.nl/research/air/wiki/Subversion502BadGateway)
[http://www.devnetwork.net/forums/viewtopic.php?p=331381](http://www.devnetwork.net/forums/viewtopic.php?p=331381) (Dont relly think this one helps at all)
[http://blog.torh.net/2007/07/25/subversion-502-bad-gateway-workaround/](http://blog.torh.net/2007/07/25/subversion-502-bad-gateway-workaround/)

**The problem:**
Thoes sites seem to do a FANTASTIC job figuring out what the error is but none of them ever get around to providing a clear way of fixing it.

**What I have tried:**
mod_gnutls - Too unstable, keeps segfaulting...
Diffrent IPs - No change
mod_rewrite - Attempted to figure it out but I think I messed it up. Too complex, however I think the fix may be with this.

What I was trying to do with the mod_rewrite
Transform the
[https://svn.mysite/path/to/file](https://svn.mysite/path/to/file)
into
[http://svn.mysite/path/to/file](http://svn.mysite/path/to/file)

But I could never get it to work. Here is the rules I used for it.
#<IfModule mod_rewrite.c>
#       RewriteEngine on
#       RewriteCond %{HTTPS} !=on
#       RewriteRule ^/svn.mysite/(.*) http://svn.mysite/$1
#</IfModule>

There was no change if I used the rules either.
^/svn.mysite/(.*)$ http://svn.mysite/$1
^/svn.mysite/(.*) https://svn.mysite/$1
^/svn.mysite/(.*)$ https://svn.mysite/$1

Also placeing [L] at the end had no effect.

However as I said I think those rules are wrong.

**Other fix options:**
*Not able to do:*
Switching to http or svnserv the connection must be encrypted.
svn+ssh is also out because I require browser support. 

*Possible:*
I am ok doing code edits are recompiling apache to work if someone can point me near the code that is messing up.
Using another web server is fine as long as it supports ssl/tls, virtual hosts, php, python, ruby, and of course svn.

---

### Post by winhamwr on 2007-11-27
I'm having pretty much the exact same issue myself with pretty much the same configuration. If I get a solution together, I'll be sure to post it back here.

---

