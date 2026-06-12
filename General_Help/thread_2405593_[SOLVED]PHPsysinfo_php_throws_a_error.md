---
title: "[SOLVED]PHPsysinfo php throws a error"
date: 2018-11-08
forum: General Help
---

### Post by sashasteph2018 on 2018-11-08
[B]any fix on this?

errorHandlerPsi :

PHP throws a error
Level : 8 Message : A non well formed numeric value encountered File : /usr/share/phpsysinfo/includes/os/class.Linux.inc.php Line : 304[HR][/HR][B]errorHandlerPsi :

**line 304.  $dev->setCache(preg_replace("/[a-zA-Z]/", "", $arrBuff[1]) * 1024);**

PHP throws a error
Level : 8 Message : A non well formed numeric value encountered File : /usr/share/phpsysinfo/includes/os/class.Linux.inc.php Line : 360[HR][/HR][B]errorHandlerPsi :

Line 360.  $dev->setCpuSpeed($buf / 1000);

PHP throws a error
Level : 8 Message : A non well formed numeric value encountered File : /usr/share/phpsysinfo/includes/os/class.Linux.inc.php Line : 363[HR][/HR][B]errorHandlerPsi :

line. 363. $dev->setCpuSpeedMax($buf / 1000);

PHP throws a error
Level : 8 Message : A non well formed numeric value encountered File : /usr/share/phpsysinfo/includes/os/class.Linux.inc.php Line : 366[HR][/HR][B]errorHandlerPsi :

line 366. $dev->setCpuSpeedMin($buf / 1000);

[B][B][B][B][B][B][B][B][B][B][B][B][B][B][B][B][B]
PHP throws a error[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][B][B][B][B][B][B][B][B][B][B][B][B]Level : 8 Message : A non well formed numeric value encountered File : /usr/share/phpsysinfo/includes/os/class.Linux.inc.php Line : 846[HR][/HR][B]errorHandlerPsi :

line 846. [B][B][B][B][B][B][B][B][B][B][B][B][B][B][B][B][B][B]$this->sys->setMemTotal($ar_buf[1] * 1024);
[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]

PHP throws a error
Level : 8 Message : A non well formed numeric value encountered File : /usr/share/phpsysinfo/includes/os/class.Linux.inc.php Line : 848[HR][/HR][B]errorHandlerPsi :

line 848. $this->sys->setMemFree($ar_buf[1] * 1024);

PHP throws a error
Level : 8 Message : A non well formed numeric value encountered File : /usr/share/phpsysinfo/includes/os/class.Linux.inc.php Line : 852[HR][/HR][B]errorHandlerPsi :

line 852 $this->sys->setMemBuffer($ar_buf[1] * 1024);

PHP throws a error
Level : 8 Message : A non well formed numeric value encountered File : /usr/share/phpsysinfo/includes/os/class.Linux.inc.php Line : 850

line 850. $this->sys->setMemCache($ar_buf[1] * 1024);[/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B][/B]

---

### Post by sashasteph2018 on 2018-11-09
Uninstalled ubuntu version for a github one

---

