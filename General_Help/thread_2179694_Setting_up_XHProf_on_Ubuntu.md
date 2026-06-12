---
title: "Setting up XHProf on Ubuntu"
date: 2013-10-09
forum: General Help
---

### Post by 3BkPKNG on 2013-10-09
(Linux beginner.)[B]

Problem[/B]

I'm trying to configure and use XHProf. I've managed to get it installed and running on my server but I get a blank page when I try to access localhost/xhprof_html. Even though I've got nothing to measure I thought this should display a config page.

This is the general post I've been following:

[http://www.grasmash.com/article/installing-xhprof-drupal#view](http://www.grasmash.com/article/installing-xhprof-drupal#view)

**Set-Up**

I'm running a fresh Ubuntu Server 13.04. Its running on a Virtual Box.

I installed xhprof using:

```
 sudo pecl install -f xhprof

```

I then added the following lines to my php.ini.

```
extension=xhprof.so
xhprof.output_dir="/tmp/xhprof"

```

I then rebooted apache and tested that xhprof is running using *php -m*. It' successfully running.

I then moved xhprof_html from ```
/usr/share/php/
``` to ```
/var/www/

```

But when I open *localhost/xhprof_html/index.php* I get a blank white screen. It's found the path but nothing displays.

I had something similar when I first installed drupal and the following command fixed it:

```
$ sudo chown -R www-data /var/www/drupal/

```
However that hasn't worked this time.

Have I set-up part of this wrong?

---

### Post by robbie2 on 2014-03-29
Try setting up a virtualhost for xhprof.

I have complete instructions here [http://www.insprinto.com.au/blog/turbocharge-your-php-with-xhprof?utm_source=linkedin&utm_campaign=xhprof&utm_medium=forum](http://www.insprinto.com.au/blog/turbocharge-your-php-with-xhprof?utm_source=linkedin&utm_campaign=xhprof&utm_medium=forum)

You can leave the code in [COLOR=#333333][FONT=Monaco]/usr/share/php/xhprof_html/ [/FONT][/COLOR]

As long as you set up a <Directory> directive for it, as shown in the guide.

> **3BkPKNG said:**
> (Linux beginner.)[B]

Problem[/B]

I'm trying to configure and use XHProf. I've managed to get it installed and running on my server but I get a blank page when I try to access localhost/xhprof_html. Even though I've got nothing to measure I thought this should display a config page.

This is the general post I've been following:

[http://www.grasmash.com/article/installing-xhprof-drupal#view](http://www.grasmash.com/article/installing-xhprof-drupal#view)

**Set-Up**

I'm running a fresh Ubuntu Server 13.04. Its running on a Virtual Box.

I installed xhprof using:

```
 sudo pecl install -f xhprof

```

I then added the following lines to my php.ini.

```
extension=xhprof.so
xhprof.output_dir="/tmp/xhprof"

```

I then rebooted apache and tested that xhprof is running using *php -m*. It' successfully running.

I then moved xhprof_html from ```
/usr/share/php/
``` to ```
/var/www/

```

But when I open *localhost/xhprof_html/index.php* I get a blank white screen. It's found the path but nothing displays.

I had something similar when I first installed drupal and the following command fixed it:

```
$ sudo chown -R www-data /var/www/drupal/

```
However that hasn't worked this time.

Have I set-up part of this wrong?

---

