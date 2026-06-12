---
title: "HTTPS returns error code -12263"
date: 2007-07-08
forum: General Help
---

### Post by mesh2005 on 2007-07-08
I followed the article:
[https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)  to configure my APACHE + SSL. Now I'm getting the following error message when requesting any page through HTTPS:
<domain name> has sent an incorrect or unexpected message (error code -12263)
I'm using Apache 2.0, PHP 4 and Ubuntu 6.06 .Please help.

---

### Post by oddstuff on 2007-09-07
I also just ran into this problem while attempting to get SSL working on a Feisty Fox LAMP installation. I would get the exact same error code but it only happened when attempting a SSL connection whereas a non-SSL connection to the same site generated no error dialog. This was consistent with different browsers although the error message differed. I found though that I had simply mis-configured my VirtualHost settings. I had one spelling error and one of the options associated with &#8216;SSLOptions&#8217; as recommended in the server guide would not work (&#8216;illegal option&#8217;) . Once I corrected these and made sure that the site was enabled (a2ensite) and restarted the server, it was no longer generating the error. So my lesson learned is always double-check your syntax. So ...

[1] check your syntax
note you can check that the virtual host syntax is correct with the following command:
# sudo apache2ctl -t -D DUMP_VHOSTS

[2] make sure the site is enabled
# sudo a2ensite fileNameForYourVirtualHostFile

[3] restart the server after making changes
# sudo apache2ctl -k restart

---

### Post by Meethoss on 2008-04-08
Thanks oddstuff, helped me fix my problem perfectly! :) (Two problems actually!)

---

