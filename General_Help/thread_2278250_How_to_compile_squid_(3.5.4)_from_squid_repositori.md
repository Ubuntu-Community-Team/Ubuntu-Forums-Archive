---
title: "How to compile squid (3.5.4) from squid repositories?"
date: 2015-05-14
forum: General Help
---

### Post by jose_torres2 on 2015-05-14
Hello.  I am new to compiling source files.

I have downloaded the squid 3.5.4 source from squid download page.  Clearly this source does not have the debian folder non less debian/rules file.

I need to use the SSL_BUMP function and according to the squid mailing lists this feature was not really bug free but until the last version (3.5.4 snapshot)

I followed the thread "http://stackoverflow.com/questions/130894/how-to-build-a-debian-ubuntu-package-from-source" using the uupdate method.

It failed asking for the new libecap dependency.  I install it the same way.  Downloaded the source from the product page as is not available in ubuntu repository and compiled succesfully (I think) using the uupdate method.

Retried the squid compile then failed again with some rules that changed on the new squid version. (--with-open-ssl change to --with-openssl, MSNT helper was changed, etc.)

I made the corrections to the rules file. Tried again, but now fails with a mime.conf file not found error.  It is not being generated correctly on the expected folder by the compilation scripts or is no longer needed and I need to turn off some setting in the rules file, or on other file.  Really do not know.  That is my question and the purpose of this post.

---

