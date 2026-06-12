---
title: "Apache ErrorDocuments"
date: 2008-01-24
forum: General Help
---

### Post by blip2 on 2008-01-24
Running: Apache v2.2

I've upgraded to Apache 2.2 recently and the ErrorDocument now seems to only do relative links (in addition to external URLs and Plain Text) For example:
ErrorDocument 404 "/web/error/error.php?code=404"
Will return:
> Not Found

The requested URL /errortest was not found on this server.

Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.
If it cause a 404. If I add error.php to /web/live/www/web/error/ it works (where /web/live/www is the site root)

Yes I have read [http://httpd.apache.org/docs/2.2/custom-error.html](http://httpd.apache.org/docs/2.2/custom-error.html) but it doesn't mention the URL being relative.

Any ideas welcome.

---

