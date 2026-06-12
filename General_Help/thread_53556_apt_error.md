---
title: "apt error"
date: 2005-08-01
forum: General Help
---

### Post by ghais on 2005-08-01
whenever i try to install or upgrade from apt-get i have the following error:
sh: dzhandle: command not found
E: Problem executing scripts DPkg::Post-Invoke 'dzhandle restart-pending-instances'
E: Sub-process returned an error code

how can i correct this?
best Rgds

---

### Post by Xian on 2005-08-01
Post the exact command you used to get that output.
In fact, duplicate it again in a terminal and post the entire session.

For example, do you get it when you run?:
```
$ sudo apt-get -f install
```

---

### Post by ktogias on 2005-08-04
Hi,

I have the same error (sorry about Greek, but I had el_GR.UTF8 in locale when i made the upgrade, and the error doesn't occur when nothing is installed.):
```

~$ sudo apt-get upgrade

&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#923;&#953;&#963;&#964;&#974;&#957; &#928;&#945;&#954;&#941;&#964;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#922;&#945;&#964;&#945;&#963;&#954;&#949;&#965;&#942; &#916;&#941;&#957;&#948;&#961;&#959;&#965; &#917;&#958;&#945;&#961;&#964;&#942;&#963;&#949;&#969;&#957;... &#927;&#955;&#959;&#954;&#955;&#951;&#961;&#974;&#952;&#951;&#954;&#949;
&#932;&#945; &#945;&#954;&#972;&#955;&#959;&#965;&#952;&#945; &#960;&#945;&#954;&#941;&#964;&#945; &#952;&#945; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#953;&#963;&#964;&#959;&#973;&#957;:
  apache2 apache2-common apache2-mpm-prefork apache2-utils bzip2 libapr0
  libbz2-1.0
7 &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#963;&#964;&#951;&#954;&#945;&#957;, 0 &#957;&#941;&#959; &#949;&#947;&#954;&#945;&#964;&#949;&#963;&#964;&#951;&#956;&#941;&#957;&#945;, 0 &#952;&#945; &#945;&#966;&#945;&#953;&#961;&#949;&#952;&#959;&#973;&#957; &#954;&#945;&#953; 0 &#948;&#949;&#957; &#945;&#957;&#945;&#946;&#945;&#952;&#956;&#943;&#950;&#959;&#957;&#964;&#945;&#953;.&#935;&#961;&#949;&#953;&#940;&#950;&#949;&#964;&#945;&#953; &#957;&#945; &#956;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#969;&#952;&#959;&#973;&#957; 1306kB/1506kB &#945;&#960;&#972; &#945;&#961;&#967;&#949;&#943;&#945;.
&#924;&#949;&#964;&#940; &#964;&#951;&#957; &#945;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#952;&#945; &#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#951;&#952;&#959;&#973;&#957; 0B &#967;&#974;&#961;&#959;&#965; &#945;&#960;&#972; &#964;&#959; &#948;&#943;&#963;&#954;&#959;.
&#920;&#941;&#955;&#949;&#964;&#949; &#957;&#945; &#963;&#965;&#957;&#949;&#967;&#943;&#963;&#949;&#964;&#949; [&#925;/&#959;]; y
&#934;&#941;&#961;&#949;:1 http://security.ubuntu.com hoary-security/main apache2-mpm-prefork 2.0.53-5ubuntu5.2 [197kB]
&#934;&#941;&#961;&#949;:2 http://security.ubuntu.com hoary-security/main apache2-common 2.0.53-5ubuntu5.2 [789kB]
&#934;&#941;&#961;&#949;:3 http://security.ubuntu.com hoary-security/main apache2-utils 2.0.53-5ubuntu5.2 [90,7kB]
&#934;&#941;&#961;&#949;:4 http://security.ubuntu.com hoary-security/main bzip2 1.0.2-2ubuntu0.2 [229kB]
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 1283kB &#963;&#949; 6m31s (3279B/s)

Preconfiguring packages ...
(&#913;&#957;&#940;&#947;&#957;&#969;&#963;&#951; &#946;&#940;&#963;&#951;&#962; &#948;&#949;&#948;&#959;&#956;&#941;&#957;&#969;&#957; ... &#960;&#961;&#959;&#962; &#964;&#959; &#960;&#945;&#961;&#972;&#957; &#949;&#947;&#954;&#945;&#964;&#945;&#963;&#964;&#940;&#952;&#951;&#954;&#945;&#957; 82547 &#945;&#961;&#967;&#949;&#943;&#945; &#954;&#945;&#953; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#953;.)
&#928;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#947;&#953;&#945; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; libbz2-1.0 1.0.2-2ubuntu0.1 (&#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; .../libbz2-1.0_1.0.2-2ubuntu0.2_i386.deb) ...
&#913;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#964;&#951;&#962; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#964;&#959;&#965; libbz2-1.0 ...
&#928;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#947;&#953;&#945; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; libapr0 2.0.53-5ubuntu5.1 (&#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; .../libapr0_2.0.53-5ubuntu5.2_i386.deb) ...
&#913;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#964;&#951;&#962; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#964;&#959;&#965; libapr0 ...
&#928;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#947;&#953;&#945; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; apache2 2.0.53-5ubuntu5.1 (&#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; .../apache2_2.0.53-5ubuntu5.2_i386.deb) ...
&#913;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#964;&#951;&#962; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#964;&#959;&#965; apache2 ...
&#928;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#947;&#953;&#945; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; apache2-mpm-prefork 2.0.53-5ubuntu5.1 (&#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; .../apache2-mpm-prefork_2.0.53-5ubuntu5.2_i386.deb) ...
 * Stopping web server (Apache2)...                                      [ ok ]
&#913;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#964;&#951;&#962; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#964;&#959;&#965; apache2-mpm-prefork ...
&#928;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#947;&#953;&#945; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; apache2-common 2.0.53-5ubuntu5.1 (&#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; .../apache2-common_2.0.53-5ubuntu5.2_i386.deb) ...
&#913;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#964;&#951;&#962; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#964;&#959;&#965; apache2-common ...
&#928;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#947;&#953;&#945; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; apache2-utils 2.0.53-5ubuntu5.1 (&#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; .../apache2-utils_2.0.53-5ubuntu5.2_i386.deb) ...
&#913;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#964;&#951;&#962; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#964;&#959;&#965; apache2-utils ...
&#928;&#961;&#959;&#949;&#964;&#959;&#953;&#956;&#945;&#963;&#943;&#945; &#947;&#953;&#945; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; bzip2 1.0.2-2ubuntu0.1 (&#967;&#961;&#951;&#963;&#953;&#956;&#959;&#960;&#959;&#953;&#974;&#957;&#964;&#945;&#962; .../bzip2_1.0.2-2ubuntu0.2_i386.deb) ...
&#913;&#960;&#959;&#963;&#965;&#956;&#960;&#943;&#949;&#963;&#951; &#964;&#951;&#962; &#945;&#957;&#964;&#953;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#964;&#959;&#965; bzip2 ...
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; libbz2-1.0 (1.0.2-2ubuntu0.2) ...

&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; libapr0 (2.0.53-5ubuntu5.2) ...

&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; apache2-utils (2.0.53-5ubuntu5.2) ...
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; apache2-common (2.0.53-5ubuntu5.2) ...

&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; apache2-mpm-prefork (2.0.53-5ubuntu5.2) ...
 * Starting web server (Apache2)...                                      [ ok ]

&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; apache2 (2.0.53-5ubuntu5.2) ...
&#915;&#943;&#957;&#949;&#964;&#945;&#953; &#949;&#947;&#954;&#945;&#964;&#940;&#963;&#964;&#945;&#963;&#951; bzip2 (1.0.2-2ubuntu0.2) ...

sh: dzhandle: command not found
E: Problem executing scripts DPkg::Post-Invoke 'dzhandle restart-pending-instances'
E: Sub-process returned an error code

```

---

### Post by blu.gecko on 2005-08-07
hold on a sec, have you updated you source.list yet? I use to get the same error.

try this

sudo gedit /etc/apt/sources.list

erase all text and paste in this text

## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

all this was found at [ubuntu guide](http://ubuntuguide.org/#extrarepositories) 


post all results.

---

### Post by ktogias on 2005-08-08
Hi,

I checked my /etc/apt/sources.list , and is just identical to that you posted, so the problem shoud not be there.....

---

### Post by enoksrd on 2005-10-01
A solution is here: [http://ubuntuforums.org/showthread.php?t=18201&highlight=dzhandle](http://ubuntuforums.org/showthread.php?t=18201&highlight=dzhandle)
I think this is a bug in the zope-common package though.  What is going on is that zope-common has been ``removed'' but not ``purged'', meaning that some config files get left behind.  In particular this includes /etc/apt/apt.conf.d/90zope-common which calls dzhandle.  dzhandle is also from zope-common, but since it isn't a conf file it gets removed when zope-common is uninstalled and hence the error.
This bug is fixed in newer Debian versions of the package.
If you do
```
sudo dpkg --purge zope-common
``` 
that should fix your problem.

---

