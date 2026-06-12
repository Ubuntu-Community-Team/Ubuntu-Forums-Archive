---
title: "lighttpd root directory is 404"
date: 2006-07-29
forum: General Help
---

### Post by viniosity on 2006-07-29
I have a working lighttpd.conf file except that when I go to the root directory I get a 404.  So I explicitly have to choose: php.foo.com/index.php instead of just php.foo.com.

Anyone else seeing this?  Here is the part of my lighttpd I think is relevant..

```

$HTTP["host"] == "php.foo.com" {
server.document-root = "/var/www/"
server.indexfiles = ( "index.php", "index.html" )
index-file.names           = ( "index.php", "index.html",
                               "index.htm", "default.htm" )
  fastcgi.server = (".php" =>
        ("localhost" =>
           ("socket" => "/tmp/phpadmin.socket",
                "bin-path" => "/usr/bin/php4-cgi -c /etc/php4/cgi/php.ini",
                "bin-environment" => (
                "PHP_FCGI_CHILDREN" => "8",
                "PHP_FCGI_MAX_REQUESTS" => "500"
                                        )
)))
}

```

**edit:**
ug.. this is the 2nd time I solved a question minutes after posting. :(

The solution was to make sure my url.rewrite was
```

url.rewrite = ( "^/$" => "index.html", "^([^.]+)$" => "$1.html" )

```
instead of:
```

url.rewrite  = ( "^/$"             => "/server-status" )

```

---

