---
title: "How to enable SSI in Apache2"
date: 2005-09-10
forum: General Help
---

### Post by tiwaris on 2005-09-10
I want to enable SSI in apache2, how to do that.

Ubuntu has somewhat tweaked and customized the apache configuration files.

I have already set the Allowoverride options and also included .htaccess files in the requisite directories, but SSI still does not work and I have to get it working asap.

Any tutorials, pointers would be useful. It used to work on my older box but now it does not. I have alredy gone through the Apache manual but am unable to rectify the problem.

Thanks
Tiwaris

---

### Post by bsussman on 2005-09-10
Try this instructional - it worked for me...

[http://www.unet.univie.ac.at/~a9826090/en/projects/linux/ubuntu-apache2-ssi.html]("http://www.unet.univie.ac.at/%7Ea9826090/en/projects/linux/ubuntu-apache2-ssi.html")

---

### Post by jnoreiko on 2005-09-24
Instead of step 2 editing the httpd.conf file, you can create a symlink to the module:

```

cd /etc/apache2/mods-enabled
sudo ln -s /etc/apache2/mods-available/include.load
```

---

### Post by jnoreiko on 2005-10-09
For the benefit of people searching for information on this: I contacted the author of the link above & got his permission to put it on the Ubuntu wiki. [https://wiki.ubuntu.com/ServerSideIncludes](https://wiki.ubuntu.com/ServerSideIncludes)

---

### Post by BobSongs on 2006-01-24
Thanks. The wiki worked just fine. The only exception was the file that was to be modified. With Apache 2 it's /etc/apache2/apache2.conf

:-)

---

### Post by takayuki on 2007-05-30
was able to enable server side includes in feisty fawn (7.04) with php5 and apache2.

thanks

---

