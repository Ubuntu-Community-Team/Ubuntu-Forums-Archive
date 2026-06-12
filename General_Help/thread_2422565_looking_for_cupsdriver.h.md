---
title: "looking for cups/driver.h"
date: 2019-07-09
forum: General Help
---

### Post by jcpfuntner on 2019-07-09
I'm trying to build a printer driver on Ubuntu 18.04.2 LTS but I'm missing cups/driver.h:

```
$ make
make  all-recursive
make[1]: Entering directory '/media/mrbruno/ExtraDrive1/Downloads/c2esp-27'
Making all in src
make[2]: Entering directory '/media/mrbruno/ExtraDrive1/Downloads/c2esp-27/src'
gcc -DHAVE_CONFIG_H -I. -I..    --pedantic -Wall -std=c99 -O2 -g -O2 -MT c2esp.o -MD -MP -MF .deps/c2esp.Tpo -c -o c2esp.o c2esp.c
c2esp.c:48:10: fatal error: cups/driver.h: No such file or directory
 #include <cups/driver.h> //has the dither functions
          ^~~~~~~~~~~~~~~
compilation terminated.
Makefile:402: recipe for target 'c2esp.o' failed
make[2]: *** [c2esp.o] Error 1
make[2]: Leaving directory '/media/mrbruno/ExtraDrive1/Downloads/c2esp-27/src'
Makefile:347: recipe for target 'all-recursive' failed
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory '/media/mrbruno/ExtraDrive1/Downloads/c2esp-27'
Makefile:287: recipe for target 'all' failed
make: *** [all] Error 2
$

```

I've seen posts that suggest installing packages and I've installed some that seemed missing - I already have others that are suggested but I am still missing the header file:

```
$ apt list | grep cups
apcupsd/bionic 3.14.14-2 amd64
apcupsd-cgi/bionic 3.14.14-2 amd64
apcupsd-doc/bionic,bionic 3.14.14-2 all
bluez-cups/bionic-updates,now 5.48-0ubuntu3.1 amd64 [installed,automatic]
brother-cups-wrapper-ac/bionic 1.0.3-1-0ubuntu4 amd64
brother-cups-wrapper-bh7/bionic 1.0.0-10-0ubuntu6 amd64
brother-cups-wrapper-common/bionic 1.0.0-10-0ubuntu7 amd64
brother-cups-wrapper-extra/bionic 1.2.1-0ubuntu4 amd64
brother-cups-wrapper-laser/bionic 2.0.1-2-0ubuntu7 amd64
brother-cups-wrapper-laser1/bionic 1.0.2-1-0ubuntu9 amd64
brother-cups-wrapper-mfc9420cn/bionic 1.0.0-1-0ubuntu7 amd64
cpdb-backend-cups/bionic 1.0.0-0ubuntu1 amd64
cups/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed]
cups-backend-bjnp/bionic 2.0.1-1 amd64
cups-browsed/bionic-updates,bionic-security,now 1.20.2-0ubuntu3.1 amd64 [installed,automatic]
cups-bsd/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
cups-client/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
cups-common/bionic-updates,bionic-updates,now 2.2.7-1ubuntu2.6 all [installed,automatic]
cups-core-drivers/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
cups-daemon/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
cups-filters/bionic-updates,bionic-security,now 1.20.2-0ubuntu3.1 amd64 [installed,automatic]
cups-filters-core-drivers/bionic-updates,bionic-security,now 1.20.2-0ubuntu3.1 amd64 [installed,automatic]
cups-ipp-utils/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
cups-pk-helper/bionic-updates,now 0.2.6-1ubuntu1.2 amd64 [installed,automatic]
cups-ppdc/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
cups-server-common/bionic-updates,bionic-updates,now 2.2.7-1ubuntu2.6 all [installed,automatic]
cups-tea4cups/bionic,bionic 3.13~alpha0+svn3565-4 all
cups-x2go/bionic,bionic 3.0.1.3-2 all
gkrellmapcupsd/bionic 0.02ubuntu1 amd64
libcups2/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed]
libcups2-dev/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed]
libcupscgi1/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
libcupsfilters-dev/bionic-updates,bionic-security,now 1.20.2-0ubuntu3.1 amd64 [installed,automatic]
libcupsfilters1/bionic-updates,bionic-security,now 1.20.2-0ubuntu3.1 amd64 [installed,automatic]
libcupsimage2/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed]
libcupsimage2-dev/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed]
libcupsmime1/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
libcupsppdc1/bionic-updates,now 2.2.7-1ubuntu2.6 amd64 [installed,automatic]
libnet-cups-perl/bionic 0.64-1 amd64
printer-driver-cups-pdf/bionic 3.0.1-5 amd64
printer-driver-hpcups/bionic,now 3.17.10+repack0-5 amd64 [installed,automatic]
python-cups/bionic 1.9.73-2 amd64
python3-cups/bionic,now 1.9.73-2 amd64 [installed,automatic]
python3-cupshelpers/bionic,bionic,now 1.5.11-1ubuntu2 all [installed,automatic]
$ 

```

Can anyone suggest what I need to install?

---

### Post by sisco311 on 2019-07-10
Hi,

If the driver is printer-driver-c2esp  (printer driver for Kodak ESP AiO color inkjet Series), then I would like to ask why do you want to build it manually. It's in the repositories:
```
sudo apt install printer-driver-c2esp
```

From where did you download the source code?

Usually there is a README or INSTALL file which contains the installation instructions.

The code is also available from the source code repository. If you enable the source repo you can use:
```
sudo apt-get build-dep printer-driver-c2esp
```to satisfy the build dependencies for the source package.

This can be useful even if the source is not from the official repo.

---

### Post by jcpfuntner on 2019-07-10
The reason I was installing from source is that I didn't know there was another option.  I was following tips in [https://ubuntuforums.org/showthread.php?t=1963303](https://ubuntuforums.org/showthread.php?t=1963303)

---

