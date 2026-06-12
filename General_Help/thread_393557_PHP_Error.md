---
title: "PHP Error"
date: 2007-03-25
forum: General Help
---

### Post by tamray on 2007-03-25
I can't find answer to this anywhere else, so any help would be greatly appreciated.

On my Ubuntu 6.10 box,  I have installed a WRE (WebGUI Runtime Environment), which does not use php. I needed a nice gallery, so I installed php, outside of the wre.  Originally I had php5, but it seemed the error might be because of that version, so I installed php4, but get the same errors.

I added the following to my webgui domain config:

LoadModule php4_module /usr/lib/apache2/modules/libphp4.so
<IfModule mod_php4.c>
 AddType application/x-httpd-php .php
#  AddType application/x-httpd-php-source .phps
</IfModule>


Now I get php pages to display properly, but am getting the following
errors when attempting to set gallery up.

Warning: preg_match: internal pcre_fullinfo() error -3 in
/data/gallery2/install/steps/AuthenticateStep.class on line 58

Warning: session_start(): Cannot send session cookie - headers already
sent by (output started at
/data/gallery2/install/steps/AuthenticateStep.class:58) in
/data/gallery2/install/index.php on line 404

Warning: session_start(): Cannot send session cache limiter - headers
already sent (output started at
/data/gallery2/install/steps/AuthenticateStep.class:58) in
/data/gallery2/install/index.php on line 404

---

