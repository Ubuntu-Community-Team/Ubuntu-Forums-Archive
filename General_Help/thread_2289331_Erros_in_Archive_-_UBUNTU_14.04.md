---
title: "Erros in Archive - UBUNTU 14.04"
date: 2015-08-03
forum: General Help
---

### Post by AnupamMitra on 2015-08-03
I installed Audacious. During the process following message was shown in  Terminal.


Reading package lists... Done
W: GPG error: [http://download.opensuse.org](http://download.opensuse.org) ./ Release: The following signatures were invalid: KEYEXPIRED 1436387333.


Errors were encountered while processing:
 /var/cache/apt/archives/libaudcore3_3.6.2-1~webupd8~trusty0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


However,  Audacious is working without any hindrance. But Synaptic Package  Manager marked it as "Broken". Therefore, no further installation of any  other software or any updating through Software Updater is being  allowed.

Therefore, need advise to overcome the impasse.

P.S. Further, l also tried to install Audacious from Ubuntu Software Centre. The outcome is as under.

installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 802502 files and directories currently installed.) 
Preparing to unpack .../libaudcore3_3.6.2-1~webupd8~trusty0_i386.deb ... 
Unpacking libaudcore3:i386 (3.6.2-1~webupd8~trusty0) over (3.6.0-1~ppa+trusty1) ... 
dpkg: error processing archive /var/cache/apt/archives/libaudcore3_3.6.2-1~webupd8~trusty0_i386.deb (--unpack): 
 trying to overwrite '/usr/lib/i386-linux-gnu/libaudgui.so.3.0.0', which is also in package libaudgui3:i386 3.6.0-1~ppa+trusty1 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Errors were encountered while processing: 
 /var/cache/apt/archives/libaudcore3_3.6.2-1~webupd8~trusty0_i386.deb 
Error in function:  
dpkg: dependency problems prevent configuration of audacious: 
 audacious depends on libaudcore3 (= 3.6.2-1~webupd8~trusty0); however: 
  Version of libaudcore3:i386 on system is 3.6.0-1~ppa+trusty1. 
 
dpkg: error processing package audacious (--configure): 
 dependency problems - leaving unconfigured

---

