---
title: "PHP does run execute on Apache"
date: 2016-05-14
forum: General Help
---

### Post by jmumby on 2016-05-14
I have installed ubuntu on a Beaglebone black. 
```

      apache2 -v
      Server version: Apache/2.4.18 (Ubuntu)
      Server built:   2016-04-15T18:00:57

      php -v
      PHP 7.0.4-7ubuntu2 (cli) ( NTS )
      Copyright (c) 1997-2016 The PHP Group
      Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies
      with Zend OPcache v7.0.6-dev, Copyright (c) 1999-2016, by Zend Technologies


```
I see this is CLI version so I guess is not used for HTTP?


Following blog posts it says to install php5 but when I try this I get "no install candidate" but as I get a php version I guess this doesn't matter?


I have added the PPA via `sudo add-apt-repository ppa:ondrej/php` and tried to install PHP5 

```

    sudo apt-get install php5 libapache2-mod-php5
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Package libapache2-mod-php5 is not available, but is referred to by another package.
    This may mean that the package is missing, has been obsoleted, or
    is only available from another source

    Package php5 is not available, but is referred to by another package.
    This may mean that the package is missing, has been obsoleted, or
    is only available from another source

    E: Package 'php5' has no installation candidate
    E: Package 'libapache2-mod-php5' has no installation candidate

```

I have created a file called info.php and added the line <?php phpinfo() ?> but when I run it it prints `<?php phpinfo() ?>` on the screen (have tried short tags as well). The file resides in `/var/www/html`.

---

### Post by spjackson on 2016-05-17
I don't think the main repositories for Ubuntu 16.04 have php5 as they have php7 instead. If you are simply wanting to get php working with apache then the following is sufficient.
```

sudo apt-get install apache2 libapache2-mod-php # n.b. without the 5

```

---

