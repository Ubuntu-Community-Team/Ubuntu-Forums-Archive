---
title: "Ubuntu Edgy unable to unset PHP E_STRICT error reporting"
date: 2006-11-08
forum: General Help
---

### Post by Saes on 2006-11-08
I have a very frustrating problem with Edgy (which also affected Dapper).  PHP5 will still report E_STRICT errors even though it isn't set in the php.ini and isn't revealed by php_info(). 

php.ini = error_reporting = E_ALL (and with E_ALL | ~E_STRICT)
php_info(); = error_reporting = 2047

I'm trying to get a PHP website up which uses PEAR DB and MySQL. I realise PEAR DB isn't OO compliant and is depreciated, this is the source of most of the errors. When E_STRICT isn't present, however, the same website works with Fedora core 5 and PHP5. I really want to stay with pear DB for the meantime to save a large rewrite. I also want to stay with Ubuntu and  run MediaWiki at it's latest version, which requires PHP5, ruling out  migrating back to PHP4. 

Does anyone have knowledge of this issue, is related to the ubuntu PHP5 or the code? Is there another way to ensure E_STRICT isn't set?

---

### Post by MikeBenza on 2006-11-08
error_reporting = E_ALL will show all errors
error_reporting = E_ALL **|** ~E_STRICT will show all errors because you're ORing a 0 (1 or 0 = 1)
error_reporting = E_ALL **&** ~E_STRICT will show all errors except strict (1 AND 0 = 0; turn off the strict bit)

- Mike

---

### Post by Saes on 2006-11-09
I resolved this error. It related to one line in the php code which was catching all the errors not reported by E_ALL. This, therefore, included the E_STRICT errors which where the source of all the problems. 

I did, however, have the logic incorrect in the php.ini, anyway. Thanks for the reply Mike!

I've left the php.ini with "error_reporting = E_ALL" and all is working.

---

