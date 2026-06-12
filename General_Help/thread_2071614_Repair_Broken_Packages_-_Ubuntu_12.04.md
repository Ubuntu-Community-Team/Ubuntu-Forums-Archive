---
title: "Repair Broken Packages - Ubuntu 12.04"
date: 2012-10-15
forum: General Help
---

### Post by Rushyang on 2012-10-15
Hey guys,

I had a fresh installation of Ubuntu 12.04 x64 and after installing Gfx Card Drivers, I tried installing Ubuntu-Restricted-Extras, which due to lack of time, I cancelled in between.

Now, I'm getting this error when I try to install anything.

Actually, I did try with force install/upgrade option, but that error won't go away. I am not able to install mp3 codecs of my player due to this.

When I open "Ubuntu Software Center", I get error message saying "Items can not be installed or removed, until your catalog is repaired. Do you want to repair it now?" when I click on repair, I get error log as below:

> installArchives() failed: perl: warning: Setting locale failed. 
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
dpkg: dependency problems prevent configuration of libsdl-image1.2:i386: 
 libsdl-image1.2:i386 depends on libjpeg62. 
dpkg: error processing libsdl-image1.2:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libwxgtk2.6-0:i386: 
 libwxgtk2.6-0:i386 depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35). 
 libwxgtk2.6-0:i386 depends on libjpeg62. 
dpkg: error processing libwxgtk2.6-0:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ttf-dejavu-extra: 
 ttf-dejavu-extra depends on defoma; however: 
  Package defoma is not installed. 
dpkg: error processing ttf-dejavu-extra (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
dpkg: dependency problems prevent configuration of ttf-dejavu: 
 ttf-dejavu depends on ttf-dejavu-extra; however: 
  Package ttf-dejavu-extra is not configured yet. 
dpkg: error processing ttf-dejavu (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 libsdl-image1.2:i386 
 libwxgtk2.6-0:i386 
 ttf-dejavu-extra 
 ttf-dejavu 
Error in function:  
dpkg: dependency problems prevent configuration of libwxgtk2.6-0:i386: 
 libwxgtk2.6-0:i386 depends on libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35). 
 libwxgtk2.6-0:i386 depends on libjpeg62. 
dpkg: error processing libwxgtk2.6-0:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libsdl-image1.2:i386: 
 libsdl-image1.2:i386 depends on libjpeg62. 
dpkg: error processing libsdl-image1.2:i386 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ttf-dejavu-extra: 
 ttf-dejavu-extra depends on defoma; however: 
  Package defoma is not installed. 
dpkg: error processing ttf-dejavu-extra (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ttf-dejavu: 
 ttf-dejavu depends on ttf-dejavu-extra; however: 
  Package ttf-dejavu-extra is not configured yet. 
dpkg: error processing ttf-dejavu (--configure): 
 dependency problems - leaving unconfigured 


This is the error log when I try to install anything from terminal (Without -f Option)
> rushyang@DarkEnergy:~$ sudo apt-get -f install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsdl-image1.2:i386 : Depends: libjpeg62:i386 but it is not going to be installed
 libwxgtk2.6-0:i386 : Depends: libesd-alsa0:i386 (>= 0.2.35) but it is not installable or
                               libesd0:i386 (>= 0.2.35) but it is not going to be installed
                      Depends: libglu1-mesa:i386 but it is not going to be installed or
                               libglu1:i386
                      Depends: libjpeg62:i386 but it is not going to be installed
 ttf-dejavu-extra : Depends: defoma but it is not going to be installed
 ubuntu-restricted-extras : Depends: ubuntu-restricted-addons but it is not going to be installed
                            Recommends: ttf-mscorefonts-installer but it is not going to be installed
                            Recommends: unrar but it is not going to be installed
                            Recommends: gstreamer0.10-plugins-bad-multiverse but it is not going to be installed
                            Recommends: libavcodec-extra-53 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Please advice asap. I want this fixed. 

Thanks You!

---

### Post by antiartist on 2012-10-15
Not to be "that guy" but you should really do a search on your problem before starting a new thread

[http://ubuntuforums.org/showthread.php?t=1980116](http://ubuntuforums.org/showthread.php?t=1980116)

---

