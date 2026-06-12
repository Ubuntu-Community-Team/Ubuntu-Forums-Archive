---
title: "build php7.4 on Xenial"
date: 2021-06-27
forum: General Help
---

### Post by rdstonegold on 2021-06-27
I followed the tut here [https://www.howtoforge.com/tutorial/how-to-compile-and-install-php-7.4-on-ubuntu-18-04/](https://www.howtoforge.com/tutorial/how-to-compile-and-install-php-7.4-on-ubuntu-18-04/). It seems to build and install correctly but i cant figure out how to link the build to the system. Ive tried 
<code>
sudo ln -s /opt/php-7.4/bin /usr/bin/php7.4/
sudo update-alternatives --install /usr/bin/php7.4 php /opt/php-7.4 90
sudo update-alternatives --set php /opt/php-7.4/bin
</code>
but it does nothing but allow me to select the linked php version but when i go to a browser or type php -v i get nothing, tells me its not there???
ive also tried adding the build directory to my path and no luck. 
Any pointers would be greatly appreciated.

---

### Post by Impavidus on 2021-06-27
Xenial is Ubuntu 16.04, which is no longer supported. Php 7.4 is the default version on Ubuntu 20.04, the current LTS release.

---

