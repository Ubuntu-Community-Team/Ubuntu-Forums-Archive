---
title: "help me install Vhcs"
date: 2008-07-04
forum: General Help
---

### Post by Mahod on 2008-07-04
hello

help me the install control panel Vhcs

this error

```
root@serv:~/vhcs2.4# make install
cd ./tools && make install
make[1]: Entering directory `/root/vhcs2.4/tools'
cd ./build && make install 
make[2]: Entering directory `/root/vhcs2.4/tools/build'
cp ./vhcs2-mkdirs.pl /usr/sbin
make[2]: Leaving directory `/root/vhcs2.4/tools/build'
cd ./daemon && make vhcs2_daemon
make[2]: Entering directory `/root/vhcs2.4/tools/daemon'
make[2]: `vhcs2_daemon' is up to date.
make[2]: Leaving directory `/root/vhcs2.4/tools/daemon'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/daemon
cp ./daemon/vhcs2_daemon /tmp/vhcs2.4/var/www/vhcs2/daemon 
make[1]: Leaving directory `/root/vhcs2.4/tools'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/etc/vhcs2
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/log/vhcs2
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/virtual
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/mail/virtual
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/log/apache2/backup
cd ./configs && make install 
make[1]: Entering directory `/root/vhcs2.4/configs'
if [[ debian == debian ]] ; then \
                cp ./vhcs2.conf /tmp/vhcs2.4/etc/vhcs2 ; \
                cd ./apache && make install ; cd .. ; \
                cd ./bind && make install ; cd .. ; \
                cd ./crontab && make install ; cd .. ; \
                cd ./database && make install ; cd .. ;  \
                cd ./init.d && make install ; cd .. ; \
                cd ./postfix && make install ; cd .. ; \
                cd ./courier && make install ; cd .. ; \
                cd ./proftpd && make install ; cd .. ; \
        fi
/bin/sh: [[: not found
make[1]: Leaving directory `/root/vhcs2.4/configs'
cd ./engine && make install 
make[1]: Entering directory `/root/vhcs2.4/engine'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/backup
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/quota
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/traffic
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/messager
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/setup
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/engine/tools
cd ./traffic && make install
make[2]: Entering directory `/root/vhcs2.4/engine/traffic'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/usr/sbin
cp  ./pflogsumm-1.1.0/pflogsumm.pl /tmp/vhcs2.4/usr/sbin
make[2]: Leaving directory `/root/vhcs2.4/engine/traffic'
cp -p -R ./vhcs2_common_code.pl /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-rqst-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-dmn-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-sub-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-als-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-htuser-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-mbox-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-serv-mngr /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./vhcs2-db-passwd /tmp/vhcs2.4/var/www/vhcs2/engine
cp -p -R ./backup/vhcs2-bk-task /tmp/vhcs2.4/var/www/vhcs2/engine/backup
cp -p -R ./backup/vhcs2-backup-all /tmp/vhcs2.4/var/www/vhcs2/engine/tools
cp -p -R ./quota/vhcs2-dsk-quota /tmp/vhcs2.4/var/www/vhcs2/engine/quota
cp -p -R ./traffic/vhcs2-srv-traff /tmp/vhcs2.4/var/www/vhcs2/engine/traffic
cp -p -R ./traffic/vhcs2-vrl-traff /tmp/vhcs2.4/var/www/vhcs2/engine/traffic
cp -p -R ./messager/vhcs2-arpl-msgr /tmp/vhcs2.4/var/www/vhcs2/engine/messager
cp -p -R ./setup/vhcs2-setup /tmp/vhcs2.4/var/www/vhcs2/engine/setup
cp -p -R ./setup/vhcs2-uninstall /tmp/vhcs2.4/var/www/vhcs2/engine/setup
cp -p -R ./tools/vhcs2-httpd-logs-mngr /tmp/vhcs2.4/var/www/vhcs2/engine/tools/vhcs2-httpd-logs-mngr
cp -p -R ./setup/vhcs2-cfg-subst /tmp/vhcs2.4/var/www/vhcs2/engine/setup
make[1]: Leaving directory `/root/vhcs2.4/engine'
cd ./gui && make install 
make[1]: Entering directory `/root/vhcs2.4/gui'
/usr/sbin/vhcs2-mkdirs.pl /tmp/vhcs2.4/var/www/vhcs2/gui
cp ./index.php /tmp/vhcs2.4/var/www/vhcs2/gui/index.php
cp ./chk_login.php /tmp/vhcs2.4/var/www/vhcs2/gui/chk_login.php
cp -dR ./admin /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./reseller /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./client /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./include /tmp/vhcs2.4/var/www/vhcs2/gui
rm -rf /tmp/vhcs2.4/var/www/vhcs2/gui/{admin,reseller,client,include}/Makefile
cp -dR ./domain_default_page /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./errordocs /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./images /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./themes /tmp/vhcs2.4/var/www/vhcs2/gui
cp -dR ./tools /tmp/vhcs2.4/var/www/vhcs2/gui
make[1]: Leaving directory `/root/vhcs2.4/gui'
```

---

