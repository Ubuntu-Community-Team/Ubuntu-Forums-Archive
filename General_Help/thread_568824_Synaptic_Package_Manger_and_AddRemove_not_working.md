---
title: "Synaptic Package Manger and Add/Remove not working"
date: 2007-10-06
forum: General Help
---

### Post by MWilliams13 on 2007-10-06
I am using Ubuntu Feisy Fawn and as the name suggests, Add/Remove and Synaptic are not working. Update Manager is also not working. 

When I click Update Manager I get this message : 

It is impossible to install or remove any software. Please use the packahge manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

I used sudo apt-get install -f and it didn't help at all.

When I open Add/Remove I get this message : 

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the information with: 'sudo apt-get update' and 'sudo apt-get install -f'.



When I open Synaptic I get this message : 

You have 1 broken package on your system!
Use the "Broken" filter to locate it.


(BTW , I have no idea what the broken filter is)


After it says that it loads all the packages and when I try is install something (I will attempt to install Amarok)   
It goes through the install process just fine until about halfway through the actual installation when I get this message 
AN ERROR OCCURED - 
The following details are provided :
E: /var/cache/apt/archives/python-uno_2.2.0-1ubuntu5_i386.deb: subprocess new pre-removal script returned error exit status 1




Any help would be nice

---

### Post by taurus on 2007-10-06
Applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by MWilliams13 on 2007-10-06
Tried all 3 multiple times. Nothing happened expect my time was lost

---

### Post by jodoj80 on 2008-01-09
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

taurus I've Festy and I could find the broken package with SYnaptic. So I try what you said in the terminal, but the last command doesn't work for me. This is the message that appears after I typed "sudo apt-get upgrade" in the terminal:
*```
****@*****:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
The following packages will be upgraded:
  app-install-data app-install-data-commercial apport apport-gtk bind9-host capplets-data cdrecord cupsys-bsd cupsys-client dbus dbus-1-utils dnsutils evolution-data-server
  evolution-data-server-common file firefox firefox-gnome-support foo2zjs genisoimage gimp gimp-data gimp-python gnome-app-install gnome-control-center gnome-media gnome-media-common gnome-panel
  gnome-panel-data gnome-system-tools hpijs hplip hwdb-client-common hwdb-client-gnome iptables libbind9-0 libcamel1.2-10 libdns22 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3 libexif12 libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libgnome-media0
  libgnome-window-settings1 libisc11 libisccc0 libisccfg1 libjasper-1.701-1 libkpathsea4 liblwres9 libmagic1 libmagick9 libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil
  libmono-system2.0-cil libmono0 libmono2.0-cil libnspr4 libnss3 libopal-2.2.0 libpanel-applet2-0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libslab0 libsmbclient
  libuuid1 libvorbis0a libvorbisenc2 libvorbisfile3 libwrap0 linux-generic linux-restricted-modules-common mesa-utils metacity metacity-common mkisofs mono-common mono-gac mono-jit mono-runtime
  openssl python-apport python-gdbm python-launchpad-bugs python-problem-report rdesktop rsync samba-common smbclient tcpdump tomboy unattended-upgrades update-manager update-manager-core
  util-linux-locales vim-common vim-tiny wodim xscreensaver-data xscreensaver-gl
119 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/86.4MB of archives.
After unpacking 115kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 88048 files and directories currently installed.)
Preparing to replace hplip 1.7.3-0ubuntu1 (using .../hplip_1.7.3-0ubuntu1.1_i386.deb) ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 284, in <module>
    process(basedir,clean_simple)
  File "/usr/sbin/update-python-modules", line 159, in process
    for dir, dirs, files in os.walk(basedir):
  File "/usr/lib/python2.5/os.py", line 286, in walk
    names = listdir(top)
TypeError: listdir() argument 1 must be (encoded string without NULL bytes), not str
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 284, in <module>
    process(basedir,clean_simple)
  File "/usr/sbin/update-python-modules", line 159, in process
    for dir, dirs, files in os.walk(basedir):
  File "/usr/lib/python2.5/os.py", line 286, in walk
    names = listdir(top)
TypeError: listdir() argument 1 must be (encoded string without NULL bytes), not str
dpkg: error processing /var/cache/apt/archives/hplip_1.7.3-0ubuntu1.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Starting HP Linux Printing and Imaging System                                                                                                                                              [ OK ] 
Preparing to replace libuuid1 1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1 (using .../libuuid1_1.39+1.40-WIP-2006.11.14+dfsg-2ubuntu1.1_i386.deb) ...
Unpacking replacement libuuid1 ...
Errors were encountered while processing:
 /var/cache/apt/archives/hplip_1.7.3-0ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
*****@*****:~$ 
```

---

### Post by PmDematagoda on 2008-01-09
Remove the file using:-
```
sudo rm /var/cache/apt/archives/hplip_1.7.3-0ubuntu1.1_i386.deb
```
That should fix the problem.

---

### Post by jodoj80 on 2008-01-09
thanks PmDematagoda, the code you told me works great. But, ](*,) this error appears after a minutes later:```
Unpacking replacement mesa-utils ...
Errors were encountered while processing:
 /var/cache/apt/archives/hplip_1.7.3-0ubuntu1.1_i386.deb
 /var/cache/apt/archives/apport_0.76.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
As you can see, appears the same package that I report in my past post with another one. Should I try the same command that you told me with both package or should I try another way in the package that still have the same problem. Sorry, but this is the first time that my ubuntu installation have so many errors.

---

### Post by PmDematagoda on 2008-01-09
Could you post the result of:-
```
cat /etc/apt/sources.list
```

---

### Post by jodoj80 on 2008-01-10
this is the command shown:
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://do.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://do.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://do.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://do.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://do.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://do.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://do.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://do.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://do.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://do.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```Thanks again PmDematagoda

---

