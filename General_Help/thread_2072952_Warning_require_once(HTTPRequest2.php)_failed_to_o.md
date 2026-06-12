---
title: "Warning: require_once(HTTP/Request2.php): failed to open stream:"
date: 2012-10-18
forum: General Help
---

### Post by CWDG on 2012-10-18
I have read many posts that tell me this is because pear is not installed. My issue is that it is installed and I have tried to re-install it without success. I have also made sure that HTTP_Request2 is installed and updated.

I have my php.ini file set to

include_path='.:/usr/share/php:/usr/share/php/pear'

I have logged into the system by ftp and the files exist and everything appears to be installed properly.

Where have I gone wrong?

FULL ERROR:

Warning: require_once(HTTP/Request2.php): failed to open stream: No such file or directory in /var/www/test.php on line 3 Fatal error: require_once(): Failed opening required 'HTTP/Request2.php' (include_path='.:/usr/share/php:/usr/share/php/pear:/usr/share/PEAR') in /var/www/test.php on line 3

LINE 3: require_once('HTTP/Request2.php');

I have other documents included using require_once() that work properly.  Could this be an issue with permissions or could I have missed a configuration of some sort?

---

