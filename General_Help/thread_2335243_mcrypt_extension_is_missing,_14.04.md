---
title: "mcrypt extension is missing, 14.04"
date: 2016-08-26
forum: General Help
---

### Post by g1387344 on 2016-08-26
My phpmyadmin shows the following error on the main page:
> The mcrypt extension is missing. Please check your PHP configuration.

I have tried literally dozens of things to get it to work, and gone through dozens of answers to similar questions, yet nothing has worked.

I've tried completely re-installing phpmyadmin, and I've followed all of these answers:

[http://askubuntu.com/questions/460837/mcrypt-extension-is-missing-in-14-04-server-for-mysql](http://askubuntu.com/questions/460837/mcrypt-extension-is-missing-in-14-04-server-for-mysql)

Yet nothing is working. 

When I output phpinfo(), it only lists mcrypt under "Additional .ini files parsed" as "/etc/php/5.6/apache2/conf.d/20-mcrypt.ini", but nowhere does it show it's enabled.

I've also tried the following, but this also didn't work:

    ```
sudo apt-get purge php5-mcrypt phpmyadmin
    sudo apt-get install php5-mcrypt phpmyadmin
```

And if this helps, here's the output for `locate mcrypt.ini`:

["]http://i.imgur.com/27Hq2h5.png]("http://i.imgur.com/27Hq2h5.png)

When I do `php -v`, the first line of the output gives me this:
    > PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php/20131226/mcrypt.so' - /usr/lib/php/20131226/mcrypt.so: cannot open shared object file: No such file or directory in Unknown on line 0

I'm using PHP 5.6 if that helps.

Please help.

---

### Post by g1387344 on 2016-08-27
Anyone?

---

