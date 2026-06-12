---
title: "Specifiy a php version from ondrej repository"
date: 2024-01-14
forum: General Help
---

### Post by dsmidgy2 on 2024-01-14
Hi,
I installed php 8.2 from Ondrej [https://ppa.launchpadcontent.net/ondrej/php/ubuntu/](https://ppa.launchpadcontent.net/ondrej/php/ubuntu/) repository on my server.
His Launchpad page: [https://launchpad.net/~ondrej/+archive/ubuntu/php/+index?field.series_filter=jammy](https://launchpad.net/~ondrej/+archive/ubuntu/php/+index?field.series_filter=jammy)

When I do a "apt upgrade" version it is trying to install php 8.3:
```

The following packages were automatically installed and are no longer required:
  php8.2-curl php8.2-gd php8.2-imap php8.2-intl php8.2-mbstring php8.2-mysql php8.2-xml php8.2-zip
Use 'sudo apt autoremove' to remove them.
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  python2.7-minimal libavdevice58 ffmpeg libopenexr25 libpostproc55
  libmagickcore-6.q16-6-extra libavcodec58 libmagickwand-6.q16-6 libpython2.7
  libavutil56 imagemagick-6.q16 libswscale5 libmagickcore-6.q16-6 monit
  libswresample3 imagemagick-6-common libavformat58 python2.7
  libpython2.7-minimal libpython2.7-stdlib libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following NEW packages will be installed:
  libapache2-mod-php8.3 php8.3-cli php8.3-common php8.3-curl php8.3-fpm php8.3-gd php8.3-imap php8.3-intl php8.3-mbstring php8.3-mysql php8.3-opcache php8.3-readline php8.3-xml php8.3-zip
The following packages will be upgraded:
  distro-info distro-info-data libapache2-mod-php libapache2-mod-php8.2 linux-firmware php-common php-curl php-fpm php-gd php-imap php-intl php-json php-mbstring php-mysql php-xml php-zip php8.2-cli
  php8.2-common php8.2-curl php8.2-fpm php8.2-gd php8.2-imap php8.2-intl php8.2-mbstring php8.2-mysql php8.2-opcache php8.2-readline php8.2-xml php8.2-zip python3-distro-info python3-software-properties
  python3-update-manager software-properties-common update-manager-core
34 upgraded, 14 newly installed, 0 to remove and 0 not upgraded.

```

And the list of installed "sury" packeges (apache, php):
```

apache2-bin/jammy,now 2.4.58-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
apache2-data/jammy,now 2.4.58-1+ubuntu22.04.1+deb.sury.org+1 all [installed]
apache2-utils/jammy,now 2.4.58-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
apache2/jammy,now 2.4.58-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
libapache2-mod-php8.2/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
libapache2-mod-php/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
libapr1/jammy,now 1.7.2-2+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
libaprutil1-dbd-sqlite3/jammy,now 1.6.3-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
libaprutil1-ldap/jammy,now 1.6.3-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
libaprutil1/jammy,now 1.6.3-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
libgd3/jammy,now 2.3.3-9+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,automatic]
libhashkit-dev/jammy,now 1.1.3-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,automatic]
libhashkit2/jammy,now 1.1.3-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,automatic]
libmemcached-dev/jammy,now 1.1.3-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
libmemcached11/jammy,now 1.1.3-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,automatic]
libmemcachedutil2/jammy,now 1.1.3-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,automatic]
libpcre2-8-0/jammy,now 10.40-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,automatic]
libpcre3/jammy,now 2:8.45-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
libxml2/jammy,now 2.9.14+dfsg-0.1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed]
php-common/now 2:93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:94+ubuntu22.04.1+deb.sury.org+1]
php-curl/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-fpm/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-gd/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-imap/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-intl/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-json/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-mbstring/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-mysql/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-xml/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php-zip/now 2:8.2+93+ubuntu22.04.1+deb.sury.org+3 all [installed,upgradable to: 2:8.3+94+ubuntu22.04.1+deb.sury.org+1]
php8.2-cli/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-common/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-curl/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-fpm/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-gd/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-imap/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-intl/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-mbstring/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-mysql/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-opcache/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-readline/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-xml/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2-zip/now 8.2.13-1+ubuntu22.04.1+deb.sury.org+1 amd64 [installed,upgradable to: 8.2.14-1+ubuntu22.04.1+deb.sury.org+1]
php8.2/jammy,now 8.2.14-1+ubuntu22.04.1+deb.sury.org+1 all [installed]

```

Is there a way to retain a php 8.2 version? I probably installed "php" instead "php8.2".

Thanks for the answer, D.

---

### Post by dsmidgy2 on 2024-01-14
Solved.

I used these commands (one package by one). Can't remove php-common. But it doesn't want to upgrade to php8.3 anymore.
apt list --installed | grep php
apt install php8.2-fpm libapache2-mod-php8.2
aptitude markauto libapache2-mod-php php-fpm php-curl php-gd php-imap php-intl php-json php-mbstring php-mysql php-xml php-zip
apt remove libapache2-mod-php php-fpm php-curl php-gd php-imap php-intl php-json php-mbstring php-mysql php-xml php-zip
aptitude unmarkauto php8.2-common
aptitude markauto php-common
apt install php8.2-zip # etc.
apt remove php-common

---

