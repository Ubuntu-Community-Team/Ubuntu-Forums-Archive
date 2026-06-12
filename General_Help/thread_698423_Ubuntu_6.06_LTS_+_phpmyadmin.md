---
title: "Ubuntu 6.06 LTS + phpmyadmin"
date: 2008-02-16
forum: General Help
---

### Post by pxlfreak on 2008-02-16
Hi,

I recently purchased a dedicated server from a provider who installed Ubuntu 6.06 LTS edition on the box with the bog standard setup.

I used apt-get install phpmyadmin to get phpmyadmin (obviously) and it installed without any errors.  

Problem I am having is accessing it via [http://mydomain.com/phpmyadmin](http://mydomain.com/phpmyadmin).

I had had a look through the forums and tried a few of the suggestions like 

sudo ln -s /usr/share/phpmyadmin /var/www

But I just get a comment back saying "File Exists".


Can someone suggest anything please?

---

### Post by eggdeng on 2008-02-16
Is there a folder in your /var/www directory called phpmyadmin? If not, look for a similarly named directory, something like MyAdmin perhaps and substitute that name for the phpmyadmin in the url.

---

### Post by pxlfreak on 2008-02-16
Yeah there is a dir called phpmyadmin in the var/www/ dir.

[http://www.pxlfreak.com/phpmyadmin/](http://www.pxlfreak.com/phpmyadmin/)

---

### Post by eggdeng on 2008-02-16
You say above you tried
> sudo ln -s /usr/share/phpmyadmin /var/www
Shouldn't that have been
```
ln -sf /usr/share/phpmyadmin /var/www/phpmyadmin
```

---

