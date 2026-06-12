---
title: "Get Php Pcntl working on Dapper"
date: 2006-07-13
forum: General Help
---

### Post by ecilento on 2006-07-13
Does anyone know how to get the pcntl functionality working in PHP5 on dapper? I've been able to get the mssql module working by following Panthar&#8217;s ([http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/]("http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/")) instructions. I tried using these same instructions but modifying the debian/rules file to have the *--enable-pcntl* under COMMON_CONFIG=. I'm not sure what I did wrong, but somewhere along the way something didn't get done so it still doesn't work. If someone could give me instructions from the beginning that would be great...

Thanks!!

---

### Post by razametal on 2006-07-19
Use :

[HTML]aptitude install php5-cli[/HTML]

---

### Post by neterslandreau on 2006-12-11
I was able to get the PHP Pcntl functions working using the following:
```

sudo apt-get install build-essential debhelper 
apt-get source php5
sudo apt-get build-dep php5
cd php5-5.1.6/debian/

```
Edit rules and in the COMMON_CONFIG section insert the line:
```

--enable-pcntl

```
(If it is not the last config option, be sure to include a backslash at the end of the line.)

Now do
```

cd ..
sudo dpkg-buildpackage

```
Remember to restart apache if necessary and everything should be fine.

---

