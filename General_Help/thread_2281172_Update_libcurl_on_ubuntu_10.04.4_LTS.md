---
title: "Update libcurl on ubuntu 10.04.4 LTS"
date: 2015-06-05
forum: General Help
---

### Post by rob134 on 2015-06-05
[COLOR=#111111][FONT=Ubuntu]I've just followed the steps on [http://pavelpolyakov.com/2014/11/17/updating-php-curl-on-ubuntu/](http://pavelpolyakov.com/2014/11/17/updating-php-curl-on-ubuntu/) in order to update curl.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When I enter** curl- V**: 
```
curl -V curl 7.39.0 (i686-pc-linux-gnu) **libcurl/7.19.7** OpenSSL/0.9.8k zlib/1.2.3.3 libidn/1.15 Protocols: tftp ftp telnet dict ldap ldaps http file https ftps Features: IDN IPv6 Largefile NTLM SSL libz
```[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]It still says my libcurl is only version 7.19.7 while it should update to 7.39, right?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I'm running Ubuntu 10.04.4 LTS[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thanks

I like to add when I enter php - V:
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]```
[/FONT][/COLOR]PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20100525+lfs/suhosin.so' - /usr/lib/php5/20100525+lfs/suhosin.so: cannot open shared object file: No such file or directory in Unknown on line 0
PHP 5.4.39-1+deb.sury.org~lucid+2 (cli) (built: Mar 24 2015 11:00:51)[COLOR=#111111][FONT=Ubuntu]
```[/FONT][/COLOR]

---

### Post by ian-weisser on 2015-06-05
Ubuntu 10.04 reached end-of-life on April 30, 2015, and is no longer supported.
We strongly advise you to update or install a supported version of Ubuntu...which will incidentally also update your version of curl.

---

### Post by rob134 on 2015-06-07
> **ian-weisser said:**
> Ubuntu 10.04 reached end-of-life on April 30, 2015, and is no longer supported.
We strongly advise you to update or install a supported version of Ubuntu...which will incidentally also update your version of curl.

Ah that's why. Ok great, good to know - thanks for that.

---

### Post by Yellow Pasque on 2015-06-08
I'm guessing you would have to do the same thing with libcurl as you did with the curl binary (link /usr/local/lib/libcurl.so.whatever to /usr/lib/libcurl.so.whatever). Otherwise, it's going to continue to use your old system copy of libcurl. That's not really recommended though (not the safe Debian/Ubuntu way of managing system libs). 

As others pointed out, 10.04 is past EOL now anyway.

---

