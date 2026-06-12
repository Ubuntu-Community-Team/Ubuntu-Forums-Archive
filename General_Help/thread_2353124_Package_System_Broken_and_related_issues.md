---
title: "Package System Broken and related issues"
date: 2017-02-19
forum: General Help
---

### Post by TAZIO39 on 2017-02-19
Hi, I'm having trouible with the issues set out below.

Running on Ubuntu 12.04 LTS 64 bit AMD and Kernel Linux 3.5.0-54-generic with GNOME 3.4.2

Any help you can offer will be welcome.

Issues:

The Package System is Broken - error message
Detail:
The following packages have unmet dependencies:

icedtea-6-jre-jamvm: Depends: openjdk-6-jre-headless (= 6b40-1.13.12-0ubuntu0.12.04.2) but 6b41-1.13.13-0ubuntu0.12.04.1 is installed
                     Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
icedtea-6-jre-jamvm:i386: Depends: openjdk-6-jre-headless (= 6b40-1.13.12-0ubuntu0.12.04.2) but 6b41-1.13.13-0ubuntu0.12.04.1 is installed
                          Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
openjdk-6-jre: Depends: openjdk-6-jre-headless (= 6b40-1.13.12-0ubuntu0.12.04.2) but 6b41-1.13.13-0ubuntu0.12.04.1 is installed
               Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is installed
               Depends: libpulse0 (>= 1:0.99.1) but 1:1.1-0ubuntu15.4 is installed
               Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.4.3-2build1 is installed
openjdk-6-jre:i386: Depends: openjdk-6-jre-headless (= 6b40-1.13.12-0ubuntu0.12.04.2) but 6b41-1.13.13-0ubuntu0.12.04.1 is installed
                    Depends: libjpeg8 (>= 8c) but 8c-2ubuntu7 is installed
                    Depends: libpulse0 (>= 1:0.99.1) but 1:1.1-0ubuntu15.4 is installed
                    Depends: libxcomposite1 (>= 1:0.3-1) but 1:0.4.3-2build1 is installed

On using Ubuntu Software Centre I get :
Error message: Package operation failed:

installArchives() failed: Error in function: 
SystemError: E:Internal Error, No file name for openjdk-6-jre-headless
Error in function: 
SystemError: E:Internal Error, No file name for openjdk-6-jre-headless
dpkg: error: parsing file '/var/lib/dpkg/status' near line 45711 package 'gwibber':
 error in Version string '3.4.2- Developers <ubuntu-devel-discuss@lists.ubuntu.com>': version string has embedded spaces
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)

Many thanks
Regards Tazio

---

### Post by RobGoss on 2017-02-19
You do realize this distribution is almost at it's end of life which will be** April 2017**, you might want to consider upgrading to the latest **16.04.2** which will have a few more years of support

Try running the following command:

```
 sudo apt-get install -f 
```

This should fix any broken pages

---

### Post by bellera on 2017-04-26
The better is to upgrade to the latest LTS, sure.
But if you need a solution for your 12.04 you can try this one (it worked for my old 12.04 systems):

sudo su
apt-get update
wget [https://launchpad.net/~openjdk-r/+archive/ubuntu/security/+build/11284063/+files/openjdk-6-jre-lib_6b40-1.13.12-0ubuntu0.12.04.2_all.deb](https://launchpad.net/~openjdk-r/+archive/ubuntu/security/+build/11284063/+files/openjdk-6-jre-lib_6b40-1.13.12-0ubuntu0.12.04.2_all.deb)
dpkg -i openjdk-6-jre-lib_6b40-1.13.12-0ubuntu0.12.04.2_all.deb
apt-get install -f
apt-get dist-upgrade

openjdk-6-jre-lib is downgraded  from 6b41 to 6b40.
And after that, all the jre packages are upgraded to 6b41, openjdk-6-jre-lib, included.
You can see this with dpkg -l | grep jre

Sorry for not using "sudo" at each line. I used "sudo su" assuming my risk.
The "dist-upgrade" is not necessary. But I done because my system had many packages for updating, including the kernel.

---

