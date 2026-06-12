---
title: "Mediawiki extentions"
date: 2007-10-24
forum: General Help
---

### Post by earobinson on 2007-10-24
Im trying to install the google analytics extension in wikimeida ([http://www.mediawiki.org/wiki/Extension:Google_Analytics](http://www.mediawiki.org/wiki/Extension:Google_Analytics)) I am editing the localsettings file and extracting the extension to the right location but I cant seem to get it to work.

Currently Im putting
> require_once("extensions/analytics.php"); in the LocalSettings.php file but the wiki page about the install says > Usage:
<analytics uacct="UA-XXXXXX-X" ></analytics> and I dont understand what that means.

Could anyone tell me?

Thanks.

---

### Post by ViRMiN on 2007-10-24
This page says you need to put your "uacct number" in the string... [http://wiki.developers.facebook.com/index.php/Google_Analytics_Example](http://wiki.developers.facebook.com/index.php/Google_Analytics_Example)

(I just did a google for "<analytics uacct="UA-XXXXXX-X" ></analytics>")

---

### Post by ViRMiN on 2007-10-24
Might want to look at this too - [http://goldensantos.com/lab/wiki/index.php/Google_Analytics](http://goldensantos.com/lab/wiki/index.php/Google_Analytics)

---

### Post by earobinson on 2007-10-24
even before I get to putting it in wkii format I get this error
> Warning: Cannot modify header information - headers already sent by (output started at /homepages/30/d220873475/htdocs/wiki/extensions/analytics.php:35) in /homepages/30/d220873475/htdocs/wiki/includes/WebResponse.php on line 10

---

### Post by earobinson on 2007-10-24
shameless bump

Well I'm getting no errors but the code is not working :( [http://wiki.earobinson.org/index.php5?title=Sandbox](http://wiki.earobinson.org/index.php5?title=Sandbox)

---

