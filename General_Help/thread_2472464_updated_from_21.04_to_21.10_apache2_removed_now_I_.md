---
title: "updated from 21.04 to 21.10 apache2 removed now I can't track down mime error"
date: 2022-02-28
forum: General Help
---

### Post by Eric.B on 2022-02-28
I realize this is more of an Apache2 mime issue, but it happened after an OS upgrade.  For some reason the upgrade removed apache2 and php7. It installed php8 but apache was wiped out.

I had to rebuild my configuration and SSL keys, but there's one new error that was not present before:
```

[I]The stylesheet [https://localhost/wp-includes/css/dist/block-library/style.min.css?ver=5.8.3](https://localhost/wp-includes/css/dist/block-library/style.min.css?ver=5.8.3) was not loaded because its MIME type, “text/html”, is not “text/css”.

[/I]
```I've tried modifying the apache2.conf file:
```

[I]SetHandler application/x-httpd-php
AddHandler application/x-httpd-php .php .htm .js .xml .htc .css .html[/I]
```


And I've tried adding the type to mime.conf
```
AddType text/css .css

```

Nothing seems to change how apache is labeling the mime types for the css and js

```
xxxx.js loaded even though its MIME type (“text/html”) is not a valid JavaScript MIME type
```

I've tried about a dozen things off stackexchange and server fault with no luck.

---

