---
title: "Error when installing lamp on Ubuntu 12.10"
date: 2013-01-17
forum: General Help
---

### Post by TipTricky on 2013-01-17
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 php5-common
 man-db
 php5-cgi
 php5-cli
 libapache2-mod-php5
 php5-gd
 php5-mysql
 dbconfig-common
 php5-mcrypt
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is the error i keep getting can any one help me get this installed???

---

### Post by d4rk0wl on 2013-01-17
You seem to have some dependency problems here. Have you already installed a lamp-stack? It is required to be installed before phpmyadmin.
```
sudo apt-get install tasksel
```
then
```
sudo tasksel install lamp
```

Once you get your lamp server running you can fix any more dependency problems by running:
```
sudo apt-get -f install
```

Regards,
- D4rk0wl

---

### Post by TipTricky on 2013-01-17
Ok ill give this a shot real quick let you know if this is solved in a bit

---

### Post by TipTricky on 2013-01-17
I get the same error when installing tasksel

---

### Post by d4rk0wl on 2013-01-18
That is odd, you shouldn't get dependencies issues while installing tasksel.

Attempt:
```
sudo apt-get -f install
```
first, and then paste the printout from terminal.

Regards,
- D4rk0wl

---

### Post by TipTricky on 2013-01-18
Yeah ill do this in the day time haha its 4:35 am and im finaly getting to bed

---

### Post by TipTricky on 2013-01-20
Sorry for the late reply been busy but heres what it says

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
10 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up php5-common (5.4.6-1ubuntu1.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing php5-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php5-cli:
 php5-cli depends on php5-common (= 5.4.6-1ubuntu1.1); however:
  Package php5-common is not configured yet.

dpkg: error processing php5-cli (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of php5-cgi:
 php5-cgi depends on php5-common (= 5.4.6-1ubuntu1.1); however:
  Package php5-common is not configured yet.

dpkg: error processing php5-cgi (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on php5-common (= 5.4.6-1ubuntu1.1); however:
  Package php5-common is not configured yet.

dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on phpapi-20100525+lfs; however:
  Package phpapi-20100525+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20100525+lfs is not configured yet.
  Package php5-cli which provides phpapi-20100525+lfs is not configured yet.
  Package php5-fpm which provides phpapi-20100525+lfs is not installed.
  Package php5-cgi which provides phpapi-20100525+lfs is not configured yet.
 php5-gd depends on php5-common (= 5.4.6-1ubuntu1.1); however:
  Package php5-common is not configured yet.

dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends on phpapi-20100525+lfs; however:
  Package phpapi-20100525+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20100525+lfs is not configured yet.
  Package php5-cli which provides phpapi-20100525+lfs is not configured yet.
  Package php5-fpm which provides phpapi-20100525+lfs is not installed.
  Package php5-cgi which provides phpapi-20100525+lfs is not configured yet.
 php5-mysql depends on php5-common (= 5.4.6-1ubuntu1.1); however:
  Package php5-common is not configured yet.

dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
Setting up man-db (2.6.3-1) ...No apport report written because MaxReports is reached already

debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up dbconfig-common (1.8.47+nmu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing dbconfig-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of php5-mcrypt:
 php5-mcrypt depends on phpapi-20100525+lfs; however:
  Package phpapi-20100525+lfs is not installed.
  Package libapache2-mod-php5 which provides phpapi-20100525+lfs is not configured yet.
  Package php5-cli which provides phpapi-20100525+lfs is not configured yet.
  Package php5-fpm which provides phpapi-20100525+lfs is not installed.
  Package php5-cgi which provides phpapi-20100525+lfs is not configured yet.

dpkg: error processing php5-mcrypt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on libapache2-mod-php5 | libapache2-mod-php5filter | php5-cgi | php5-fpm | php5; however:
  Package libapache2-mod-php5 is not configured yet.
  Package libapache2-mod-php5filter is not installed.
  Package php5-cgi is nNo apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                 ot configured yet.
  Package php5-fpm is not installed.
  Package php5 is not installed.
 phpmyadmin depends on php5-mysql | php5-mysqli | php5-mysqlnd; however:
  Package php5-mysql is not configured yet.
  Package php5-mysqli is not installed.
  Package php5-mysqlnd is not installed.
 phpmyadmin depends on php5-mcrypt; however:
  Package php5-mcrypt is not configured yet.
 phpmyadmin depends on dbconfig-common; however:
  Package dbconfig-common is not configured yet.

dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 php5-common
 php5-cli
 php5-cgi
 libapache2-mod-php5
 php5-gd
 php5-mysql
 man-db
 dbconfig-common
 php5-mcrypt
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by TipTricky on 2013-01-20
Now when i try to install anything with software center it says can not install until package catalog is repair but when i click repair it says unable to uninstall/install package

---

### Post by d4rk0wl on 2013-01-20
It appears you have some unused packages. Try this:
```
sudo apt-get autoremove
```

Then attempt the same:
```
sudo apt-get -f install
```

If still no luck try purging the attempted install of phpmyadmin:
```
sudo apt-get purge phpmyadmin; sudo apt-get autoremove -y
```

Hope this helps.

Regards,
- D4rk0wl

---

### Post by TipTricky on 2013-01-20
This is what that gives me...

```
tiptricky@tiptricky-GT5622:~$ sudo apt-get autoremove
[sudo] password for tiptricky: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.5.0-22-generic : Depends: linux-image-3.5.0-22-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.5.0-22-generic but it is not installed
E: Unmet dependencies. Try using -f.

tiptricky@tiptricky-GT5622:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.5.0-22-generic
Suggested packages:
  fdutils linux-doc-3.5.0 linux-source-3.5.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.5.0-22-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 0 B/11.6 MB of archives.
After this operation, 25.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 222187 files and directories currently installed.)
Unpacking linux-image-3.5.0-22-generic (from .../linux-image-3.5.0-22-generic_3.5.0-22.34_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-22-generic_3.5.0-22.34_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.5.0-22-generic_3.5.0-22.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

tiptricky@tiptricky-GT5622:~$ sudo apt-get purge phpmyadmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.5.0-22-generic : Depends: linux-image-3.5.0-22-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.5.0-22-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Cheesehead on 2013-01-28
> **TipTricky said:**
> 
tiptricky@tiptricky-GT5622:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.5.0-22-generic
Suggested packages:
  fdutils linux-doc-3.5.0 linux-source-3.5.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.5.0-22-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 0 B/11.6 MB of archives.
After this operation, 25.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 222187 files and directories currently installed.)
Unpacking linux-image-3.5.0-22-generic (from .../linux-image-3.5.0-22-generic_3.5.0-22.34_i386.deb) ...
**[COLOR="Red"]debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process:[/COLOR]** Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/linux-image-3.5.0-22-generic_3.5.0-22.34_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-22-generic /boot/vmlinuz-3.5.0-22-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.5.0-22-generic_3.5.0-22.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Seems like you had another package manager open at the time. Don't do that.


1) Exit ALL package managers. All of them. Even Software Center.
2) run [FONT="Courier New"]sudo apt-get update[/FONT]
3) run [FONT="Courier New"]sudo apt-get -f install[/FONT]

Post any error message here.

---

### Post by Old_Grey_Wolf on 2013-01-28
Have you used this commend to upgrade? It looks like the problem is kernel version related.

```
sudo apt-get dist-upgrade
```

---

