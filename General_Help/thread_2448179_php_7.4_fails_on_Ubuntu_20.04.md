---
title: "php 7.4 fails on Ubuntu 20.04"
date: 2020-08-03
forum: General Help
---

### Post by Rein_Mann on 2020-08-03
I have Ubuntu 20.04 running on 2 devices. (amd64 and armhf) I have installed a lamp server on both devices. The php 7.4 supplied with the distribution does not seen to work. The output of the php files produces the 'code' instead of the 'forms'. The same installation on Debian 9 (php version 7.0) works perfectly. Can someone help with solving this issue?
R.

---

### Post by jp734 on 2020-08-04
What happens when you enter 127.0.0.1 on your browser? Is apache running?
Also, check if you have "libapache2-mod-php7.4" installed

---

### Post by Rein_Mann on 2020-08-06
Yes. Apache2 is running . My web site is up. libapache2-mod-php installed. Instead of the php forms I get the code of the particular files displayed.

---

### Post by SeijiSensei on 2020-08-06
Try
```
sudo a2enmod php7.4
```

On my machine with PHP working I get
```

Considering dependency mpm_prefork for php7.4:
Considering conflict mpm_event for mpm_prefork:
Considering conflict mpm_worker for mpm_prefork:
Module mpm_prefork already enabled
Considering conflict php5 for php7.4:
Module php7.4 already enabled

```

---

### Post by Rein_Mann on 2020-08-06
[ 						 							 						 					]("https://ubuntuforums.org/member.php?u=698195") 				 				 					 						 	[**[COLOR=#000000]SeijiSensei: Checked all. No change[/COLOR]**]("https://ubuntuforums.org/member.php?u=698195") , info.php shows a blank page, other php files show the code.

---

### Post by dragonfly41 on 2020-08-07
Some ideas ..
(a) Tried clearing browser cache?
(b) Cleared out any hidden .htaccess files?
(c) Tried running ```
php -m
```

---

### Post by jp734 on 2020-08-07
If none of the above works, check your log files and post?

---

### Post by sdsurfer on 2020-08-07
> The output of the php files produces the 'code' instead of the 'forms'

This is going to most likely be a configuration issue, not a PHP or OS issue.

If you can run php -version and get a response, PHP is fine.

Google around for "php doesn't execute," it is most likely an Apache config - php module commented out, no handlers for PHP in the domain, there are a couple reasons and they will all be very simple once you find them. :-D

---

### Post by SeijiSensei on 2020-08-07
You aren't using "short tags" are you?  See /etc/php/7.4/apache2/php.ini:

```

; This directive determines whether or not PHP will recognize code between
; <? and ?> tags as PHP source which should be processed as such. It is
; generally recommended that <?php and ?> should be used and that this feature
; should be disabled, as enabling it may result in issues when generating XML
; documents, however this remains supported for backward compatibility reasons.
; Note that this directive does not control the <?= shorthand tag, which can be
; used regardless of this directive.
; Default Value: On
; Development Value: Off
; Production Value: Off
; [http://php.net/short-open-tag](http://php.net/short-open-tag)
short_open_tag = Off

```

---

