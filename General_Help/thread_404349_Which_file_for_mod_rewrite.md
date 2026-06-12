---
title: "Which file for mod_rewrite?"
date: 2007-04-08
forum: General Help
---

### Post by Peter Mount on 2007-04-08
Hello

I'm trying to use .htacess in localhost to test url rewriting on my home computer before uploading a web blog. Which file in Ubuntu Edgy should I install mod_rewrite in? I understand I need to use the lines

LoadModule rewrite_module modules/mod_rewrite.so
AddModule mod_rewrite.c

I understand the httpd.conf file in in Apache2 in Ubuntu Edgy is only used for backward compatibility

Thanks

---

### Post by Peter Mount on 2007-04-08
Hi 

I  managed to fix my problem.

First I tried the instructions at:

[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

That didn't work but then I found instructions at:

[http://attic.krampo.info/2006/01/31/howto-enable-mod_rewrite-apache2-ubuntu/](http://attic.krampo.info/2006/01/31/howto-enable-mod_rewrite-apache2-ubuntu/)

Now it works.

I don't know yet if one set of instructions depends on the other but I've just had some eggs on toast with a nice coffee so I don't really mind how it works at the moment

Have fun

---

