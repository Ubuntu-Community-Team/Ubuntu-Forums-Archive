---
title: "Apache2Reverse Proxy 403 Problem"
date: 2008-04-17
forum: General Help
---

### Post by cbailey on 2008-04-17
Here's my config files for apache:

```
-----------------------   File: /etc/apache2/mods-enabled/proxy.conf    -------------------

<IfModule mod_proxy.c>
        #turning ProxyRequests on and allowing proxying from all may allow
        #spammers to use your proxy to send email.

        #(On when Testing)
        ProxyRequests Off 

        <Proxy *>
                AddDefaultCharset off
                Order Deny,Allow
                #Deny from all
                Allow from all
                #Allow from .example.com

                # Define the character set for proxied FTP directory listings
                ProxyFtpDirCharset UTF-8
        </Proxy>

        # Enable/disable the handling of HTTP/1.1 "Via:" headers.
        # ("Full" adds the server version; "Block" removes all outgoing Via: headers)
        # Set to one of: Off | On | Full | Block

        ProxyVia On
</IfModule>
---------------------------------------------------------------------------------
```

```

-------------------------     File: /etc/apache2/httpd.conf     -------------------

ServerName website.com

ProxyPass /directory http://www.google.com
ProxyPassReverse /directory http://www.google.com

-----------------------------------------------------------------------
```

Why does [http://www.website.com/directory](http://www.website.com/directory) give me 403 Forbidden, not google.com page?

Ubuntu 7.04 Feisty Fawn (Client Edition)
Apache 2.2.3 works fine.

I'm confused, and there isn't much out there (trust me, I looked). Any help is welcome.

Thanks

Cbailey

NB: Just in case you are wondering, no, the addresses above aren't mine, nor do I administer them. they are substituted for my actual addy. I was testing with google, but still, no success.

---

### Post by comandrei on 2008-04-17
I don't know if I get it right, but from what you wrote there you're trying to serve content from google.com , server wich probably dosen't allow that method. That's probably the reason you're getting 403. You could proxy with lighttpd to reduce apache's load, like here :[http://www.linux.com/feature/51673](http://www.linux.com/feature/51673)

---

### Post by cbailey on 2008-04-17
Hi

Yeah, was just using the google page for testing.

Actually trying to pull a webpage from my local network devices into my website hosted on that apache build.

Thing is, Lighttpd needs proxy as well, and that's where the problem is.

Hmmmm.

Thanks though - some input is better than none.

Cbailey

---

