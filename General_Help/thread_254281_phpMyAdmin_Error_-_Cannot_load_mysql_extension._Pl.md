---
title: "phpMyAdmin Error - Cannot load mysql extension. Please check your PHP configuration"
date: 2006-09-09
forum: General Help
---

### Post by JD_2020 on 2006-09-09
Hi -

Well I battled for hours on end getting my MySQL server to be setup and configured properly (i.e. authenticate the root user properly). Now that all of that stuff is set, I installed phpMyAdmin.

Well when I go to phpMyAdmin via my web browser, I get a page that says:

phpMyAdmin - Error

Cannot load mysql extension. Please check your PHP configuration. - Documentation

I googled that error, and all the results suggested a problem with my php.ini file - but all the solutions had to deal with .DLL files (and since those are Windows I figured the solutions would obviously not apply for me).

Any ideas?

Thanks!

---

### Post by az_human on 2006-09-09
Add the following line to your PHP.INI file:

extension=mysql.so

---

### Post by JD_2020 on 2006-09-10
I did that and rebooted the whole machine and still I get the same error when I go to load phpMyAdmin.

---

### Post by az on 2006-09-10
> **JD_2020 said:**
> Hi -

Well I battled for hours on end getting my MySQL server to be setup and configured properly (i.e. authenticate the root user properly). Now that all of that stuff is set, I installed phpMyAdmin.

Well when I go to phpMyAdmin via my web browser, I get a page that says:

phpMyAdmin - Error

Cannot load mysql extension. Please check your PHP configuration. - Documentation

I googled that error, and all the results suggested a problem with my php.ini file - but all the solutions had to deal with .DLL files (and since those are Windows I figured the solutions would obviously not apply for me).

Any ideas?

Thanks!
How did you install the Lamp stack?

See here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by az_human on 2006-09-11
Maybe you don't have the PHP MySQL extension installed?

---

### Post by JD_2020 on 2006-09-15
I have no idea what to do. I am really really frustrated.

My mysql extensions should be installed. I had phpMyAdmin working at one point, but then I had to uninstall it after I re-installed apache2. Then I changed from cookie to http authentication, I had some problems with my root user on MySQL, and during the chaos phpMyAdmin broke.

There is just no reason it shouldn't be working now. Like I said, it worked at one point (but had no authentication) so I know it works. I even tried un-doing all the chnages I made to make sure it authenticates, but now it is broken.

Any ideas?

---

