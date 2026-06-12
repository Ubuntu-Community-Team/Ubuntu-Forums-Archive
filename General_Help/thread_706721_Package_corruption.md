---
title: "Package corruption"
date: 2008-02-24
forum: General Help
---

### Post by Tatty on 2008-02-24
yesterday my computer decided it was due for an fsck check, so it ran on boot.  It returned an incredible amount of errors - i really have no idea what caused this as i have never had such problems before - and it dumped me to a root CLI and asked me to run fsck manually, which I did, and got it to fix all the errors.

Then upon rebooting, everything seemed to be working fine and i carried on as usual.  Then i tried to install xsensors and it failed...

```
tatty@MythServer:~$ sudo apt-get install xsensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lm-sensors
Suggested packages:
  sensord read-edid
The following NEW packages will be installed
  lm-sensors xsensors
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/535kB of archives.
After unpacking 1761kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `makedev' missing, assuming package has no files currently installed.
 after fsck
dpkg: serious warning: files list file for package `firestarter' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgcrypt11' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `fontconfig' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libpam0g' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libsamplerate0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openssl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `sysv-rc' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `liblzo2-2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libthai-data' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libreadline5' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gs-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gftp-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-central' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `dpkg' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `aptitude' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gconf2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python-apt' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/lm-sensors_1%3a2.10.4-1ubuntu1_i386.deb (--unpack):
 unable to open files list file for package `libglew1.4': No such device or address
Errors were encountered while processing:
 /var/cache/apt/archives/lm-sensors_1%3a2.10.4-1ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
tatty@MythServer:~$ 

```

It seems to do this for any package i try to install now.

I have tried:

sudo apt-get install -f
sudo apt-get clean
sudo apt-get build-dep xsensors
sudo apt-get check

Really stuck now, also if anyone knows any utilities i can check the red/write integritry of my HDD with, that would be great. thanks.

---

### Post by sumguy231 on 2008-02-24
Ouch, my condolences regarding your filesystem. If you want to check your hard drive's health there is probably something on the Ultimate Boot CD which you can use:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

Hopefully it is just the filesystem and not the device itself.

---

