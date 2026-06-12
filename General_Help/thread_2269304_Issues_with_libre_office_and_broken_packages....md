---
title: "Issues with libre office and broken packages..."
date: 2015-03-14
forum: General Help
---

### Post by pd5 on 2015-03-14
I'm using Ubuntu 14.
I was fed up with the lack of english fonts in Libre Office and it's slowness. I thought I'd download Open Office instead, since it sounded SOO simple to do.
It's not. Ubuntu threw fits over it and still is.
I tried to remove Libre and install Op O.
At this point, I can't open any documents or download anything to help resolve it.
I have a "Error-BrokenCount >0"  error message
When I run apt-get install -f  : as suggested in the Terminal.
I run into more errors - 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
20 not fully installed or removed.
Need to get 0 B/19.9 MB of archives.
After this operation, 76.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 205804 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb ...
Unpacking libreoffice-common (1:4.2.7-0ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.1-9775
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/prereg/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/program/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

- I feel like I'm running in circles. Can anyone give me some help ? IF Open Office was truly compatible with Ubuntu 14, I would prefer that, but if not, I'll go with Libre Office. I just want the simplest, most compatible solution. I've spent a lot of time searching around for some potential solutions, have found some dead ends and some circular solutions. No real solutions yet. ](*,)

I read that installing synaptic is good, bc it's a stronger program for fixing such issues, but I can't install anything right now - 

Please advise and Thank You in advance !

PD:guitar:

---

### Post by gifford on 2015-03-14
I would do sudo apt-get purge openoffice
and sudo apt-get purge libreoffice

Then reinstall libreoffice. And yes, you could use synaptic but sudo apt-get install libreoffice should work fine for you.
You may want to restart your computer before installing again.

---

### Post by flaymond on 2015-03-14
Try this -

```
 sudo apt-get -f install || sudo dpkg --configure -a || sudo apt-get update || sudo apt-get purge openoffice libreoffice && sudo apt-get install libreoffice || sudo apt-get autoremove || sudo apt-get clean 
```

This will fix dpkg using standard commands, update, purging (remove) open office and libreoffice then re-install libreoffice and clean any junk dowloaded files.

If it not working, reboot your pc then try this command again. If not worked, please post the errors.

---

### Post by pd5 on 2015-03-14
pd@pd-MM061:~$ sudo apt-get purge openoffice
[sudo] password for pd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package openoffice
pd@pd-MM061:~$ sudo apt-get purge libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.2.7) but it is not going to be installed
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

gonna reboot then try your idea Inter.

---

### Post by pd5 on 2015-03-14
rebooted, ran commands. errors. rebooted, ran commands, looked to be the same errors :

```
pd@pd-MM061:~$  sudo apt-get -f install || sudo dpkg --configure -a || sudo apt-get update || sudo apt-get purge openoffice libreoffice && sudo apt-get install libreoffice || sudo apt-get autoremove || sudo apt-get clean
[sudo] password for pd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
20 not fully installed or removed.
Need to get 19.9 MB of archives.
After this operation, 76.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main libreoffice-common all 1:4.2.7-0ubuntu2 [19.9 MB]
Fetched 19.9 MB in 23s (841 kB/s)                                              
(Reading database ... 205804 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb ...
Unpacking libreoffice-common (1:4.2.7-0ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.1-9775
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/prereg/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/program/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of libreoffice-java-common:
 libreoffice-java-common depends on libreoffice-common; however:
  Package libreoffice-common is not installed.

dpkg: error processing package libreoffice-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-sdbc-hsqldb:
 libreoffice-sdbc-hsqldb depends on libreoffice-java-common (>= 1:4.2.7~); however:
  Package libreoffice-java-common is not configured yet.

dpkg: error processing package libreoffice-sdbc-hsqldb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:4.2.7); however:
  Package libreoffice-common is not installed.

dpkg: error processing package libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice:
 libreoffice depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.
 libreoffice depends on libreoffice-impress; however:
  Package libreoffice-impress is not configured yet.
 libreoffice depends on libreoffice-math; however:
  Package libreoffice-math is not configured yet.
 libreoffice depends on libreoffice-java-common (>= 1:4.2.7~); however:
  Package libreoffice-java-common is not configured yet.
 libreoffice depends on python3-uno (>= 4.0~); however:
  Package python3-uno is not configured yet.

dpkg: error processing package libreoffice (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mythes-en-us:
 mythes-en-us depends on libreoffice-core | openoffice.org-core (>= 1.9) | language-support-writing-en; however:
  Package libreoffice-core is not configured yet.
  Package openoffice.org-core is not installed.
  Package language-support-writing-en is not installed.

dpkg: error processing package mythes-en-us (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-base-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-base-core is not configured yet.
 libreoffice-base depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-sdbc-firebird:
 libreoffice-sdbc-firebird depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-sdbc-firebird (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.
 libreoffice-report-builder-bin depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-pdfimport:
 libreoffice-pdfimport depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-pdfimport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-avmedia-backend-gstreamer:
 libreoffice-avmedia-backend-gstreamer depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-avmedia-backend-gstreamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-drivers:
 libreoffice-base-drivers depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-base-drivers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-base-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-base-core is not configured yet.
 libreoffice-calc depends on libreoffice-core (= 1:4.2.7-0ubuntu2); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing package libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libreoffice-java-common
 libreoffice-sdbc-hsqldb
 libreoffice-core
 python3-uno
 libreoffice-math
 libreoffice-impress
 libreoffice
 libreoffice-writer
 mythes-en-us
 libreoffice-base-core
 libreoffice-gnome
 libreoffice-base
 libreoffice-sdbc-firebird
 libreoffice-report-builder-bin
 libreoffice-pdfimport
 libreoffice-avmedia-backend-gstreamer
 libreoffice-gtk
 libreoffice-base-drivers
 libreoffice-draw
 libreoffice-calc
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [62.0 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [439 kB]  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [259 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Fetched 761 kB in 7s (97.7 kB/s)                                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libreoffice is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.2.7) but it is not going to be installed
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.2.7) but it is not installed
 libreoffice-java-common : Depends: libreoffice-common but it is not installed
E: Unmet dependencies. Try using -f.
pd@pd-MM061:~$ 
```


What's next ? Any thoughts ?

---

### Post by Bucky Ball on 2015-03-14
Please use [code] tags for terminal output. See the last link in my signature for how. Remember, OO and LO are fairly much identical in a lot of ways, so not sure you are going to see much difference in performance or fonts. Unsure what you mean by 'not many English fonts'. If you mean regualr fonts generally found in Word or MS, I have a heap. Have you installed MS core fonts? ubuntu-restricted-extras drags them in from memory or you can install directly.

---

### Post by pd5 on 2015-03-14
Agreed, I could install the MS Core fonts. At this point, I'm just trying to get the machine working again...
Thanks Bucky.

---

### Post by deadflowr on 2015-03-15
Try
```
sudo apt-get purge openoffice*
```
Then try the sudo apt-get install -f command.
The whole problem, as I see it, is that you have the soffice.bin file being used by openoffice.
This is causing libreoffice-common to freak out.

openoffice has no super metapackage that I know of so removing only openoffice would probably only remove one package.
By adding the * symbol at the end of openoffice, it should remove all packages prefixed with openoffice, including openoffice-common, or -writer, or -what have you.

well, that is my thinking on the matter anyway.

---

### Post by Bucky Ball on 2015-03-15
And I like deadflowr's thinking. For future reference, and as you've found out, OO and SO can not be installed at the same time. One must be completely purged prior to installing the other. This is sometimes problematic.

---

### Post by pd5 on 2015-03-15
Bucky - nope, never tried to install them both at the same time.
Libre came with Ubuntu 14 - tried to remove, then install OO - wouldn't go- some leftovers from libre remained ? - idk.

ok deadflower-  here's what it kicked out :

LOOKS like OO got removed, but still kicking out errors, etc.
```

pd@pd-MM061:~$ sudo apt-get purge openoffice*
[sudo] password for pd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openoffice.org-hyphenation-pl' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-pt' for regex 'openoffice*'
Note, selecting 'libopenoffice-oodoc-perl' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ro' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ru' for regex 'openoffice*'
Note, selecting 'libming-fonts-openoffice' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sh' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sk' for regex 'openoffice*'
Note, selecting 'openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sl' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sr' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-sv' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ui' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-uk' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-de-ch' for regex 'openoffice*'
Note, selecting 'openoffice.org-dmaths' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-en-au' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-zu' for regex 'openoffice*'
Note, selecting 'openoffice.org-dev-doc' for regex 'openoffice*'
Note, selecting 'openoffice.org-calc' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-en-us' for regex 'openoffice*'
Note, selecting 'openofficeorg-desktop-integration' for regex 'openoffice*'
Note, selecting 'openoffice.org-debian-menus' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-an' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ca' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-en-us' for regex 'openoffice*'
Note, selecting 'openoffice.org2-thesaurus' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-eo' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-es' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-eu' for regex 'openoffice*'
Note, selecting 'mozilla-openoffice.org' for regex 'openoffice*'
Note, selecting 'openoffice.org-writer' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-fo' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-gl' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-en-us' for regex 'openoffice*'
Note, selecting 'openoffice.org-base' for regex 'openoffice*'
Note, selecting 'openoffice.org-bundled' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-ca' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-cs' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-de' for regex 'openoffice*'
Note, selecting 'openoffice.org-kde' for regex 'openoffice*'
Note, selecting 'openoffice.org-common' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-fr' for regex 'openoffice*'
Note, selecting 'openoffice-desktop-integration' for regex 'openoffice*'
Note, selecting 'openoffice.org-core' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-af' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nb' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-hu' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nn' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-nr' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ns' for regex 'openoffice*'
Note, selecting 'kde-thumbnailer-openoffice' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-it' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ca' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-cs' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-da' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-de' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-el' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-en' for regex 'openoffice*'
Note, selecting 'openoffice.org-hunspell' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-es' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-fr-fr' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-fi' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-fr' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ss' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-st' for regex 'openoffice*'
Note, selecting 'openoffice.org-dtd-officedocument1.0' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-ga' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-ne' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-tl' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-tn' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-hr' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-hu' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-id' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-uz' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-is' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-it' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-pl' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-ve' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-at' for regex 'openoffice*'
Note, selecting 'openoffice-debian-menus' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-ro' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-xh' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-ru' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-lt' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-ch' for regex 'openoffice*'
Note, selecting 'openoffice.org-thesaurus-sk' for regex 'openoffice*'
Note, selecting 'openoffice.org-unbundled' for regex 'openoffice*'
Note, selecting 'openoffice.org-updatedicts' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-de-de' for regex 'openoffice*'
Note, selecting 'openoffice.org-spellcheck-zu' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation-nl' for regex 'openoffice*'
Note, selecting 'openoffice.org-hyphenation' for regex 'openoffice*'
Package 'openoffice.org-thesaurus-it' is not installed, so not removed
Note, selecting 'dictionaries-common' instead of 'openoffice.org-updatedicts'
Package 'openoffice.org-hunspell' is not installed, so not removed
Package 'openoffice.org-core' is not installed, so not removed
Note, selecting 'hunspell-an' instead of 'openoffice.org-spellcheck-an'
Package 'openoffice.org' is not installed, so not removed
Package 'openoffice.org-spellcheck-en-us' is not installed, so not removed
Note, selecting 'hunspell-eu-es' instead of 'openoffice.org-spellcheck-eu'
Note, selecting 'hunspell-gl-es' instead of 'openoffice.org-spellcheck-gl'
Note, selecting 'hunspell-uz' instead of 'openoffice.org-spellcheck-uz'
Package 'openoffice.org-writer' is not installed, so not removed
Note, selecting 'hyphen-af' instead of 'openoffice.org-hyphenation-af'
Note, selecting 'hyphen-ca' instead of 'openoffice.org-hyphenation-ca'
Note, selecting 'hyphen-de' instead of 'openoffice.org-hyphenation-de'
Note, selecting 'hyphen-en-us' instead of 'openoffice.org-hyphenation-en-us'
Package 'openoffice.org-hyphenation-hr' is not installed, so not removed
Note, selecting 'hyphen-hu' instead of 'openoffice.org-hyphenation-hu'
Note, selecting 'hyphen-it' instead of 'openoffice.org-hyphenation-it'
Note, selecting 'hyphen-pl' instead of 'openoffice.org-hyphenation-pl'
Note, selecting 'hyphen-ro' instead of 'openoffice.org-hyphenation-ro'
Note, selecting 'hyphen-ru' instead of 'openoffice.org-hyphenation-ru'
Note, selecting 'hyphen-sh' instead of 'openoffice.org-hyphenation-sh'
Note, selecting 'hyphen-sl' instead of 'openoffice.org-hyphenation-sl'
Note, selecting 'hyphen-sr' instead of 'openoffice.org-hyphenation-sr'
Package 'openoffice.org-hyphenation-zu' is not installed, so not removed
Note, selecting 'hyphen-zu' instead of 'openoffice.org-hyphenation-ui'
Package 'openoffice.org-base' is not installed, so not removed
Package 'openoffice.org-common' is not installed, so not removed
Package 'openoffice.org-dev-doc' is not installed, so not removed
Note, selecting 'myspell-ca' instead of 'openoffice.org-spellcheck-ca'
Note, selecting 'myspell-eo' instead of 'openoffice.org-spellcheck-eo'
Note, selecting 'myspell-es' instead of 'openoffice.org-spellcheck-es'
Note, selecting 'myspell-fo' instead of 'openoffice.org-spellcheck-fo'
Note, selecting 'myspell-nb' instead of 'openoffice.org-spellcheck-nb'
Note, selecting 'myspell-nn' instead of 'openoffice.org-spellcheck-nn'
Note, selecting 'myspell-nr' instead of 'openoffice.org-spellcheck-nr'
Note, selecting 'myspell-ns' instead of 'openoffice.org-spellcheck-ns'
Note, selecting 'myspell-ss' instead of 'openoffice.org-spellcheck-ss'
Note, selecting 'myspell-st' instead of 'openoffice.org-spellcheck-st'
Note, selecting 'myspell-tn' instead of 'openoffice.org-spellcheck-tn'
Note, selecting 'myspell-ve' instead of 'openoffice.org-spellcheck-ve'
Note, selecting 'myspell-xh' instead of 'openoffice.org-spellcheck-xh'
Note, selecting 'myspell-zu' instead of 'openoffice.org-spellcheck-zu'
Note, selecting 'mythes-ca' instead of 'openoffice.org-thesaurus-ca'
Note, selecting 'mythes-cs' instead of 'openoffice.org-thesaurus-cs'
Note, selecting 'mythes-de' instead of 'openoffice.org-thesaurus-de'
Note, selecting 'mythes-de-ch' instead of 'openoffice.org-thesaurus-de-ch'
Note, selecting 'mythes-en-au' instead of 'openoffice.org-thesaurus-en-au'
Note, selecting 'mythes-en-au' instead of 'openoffice.org2-thesaurus'
Note, selecting 'mythes-en-us' instead of 'openoffice.org-thesaurus-en-us'
Note, selecting 'mythes-fr' instead of 'openoffice.org-thesaurus-fr'
Note, selecting 'mythes-hu' instead of 'openoffice.org-thesaurus-hu'
Note, selecting 'mythes-ne' instead of 'openoffice.org-thesaurus-ne'
Note, selecting 'mythes-pl' instead of 'openoffice.org-thesaurus-pl'
Note, selecting 'mythes-ro' instead of 'openoffice.org-thesaurus-ro'
Note, selecting 'mythes-ru' instead of 'openoffice.org-thesaurus-ru'
Note, selecting 'mythes-sk' instead of 'openoffice.org-thesaurus-sk'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-cs'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-da'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-el'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-es'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-fi'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-ga'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-id'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-is'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-nl'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-pt'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-sk'
Note, selecting 'hyphen-sv' instead of 'openoffice.org-hyphenation-sv'
Note, selecting 'openoffice.org-hyphenation' instead of 'openoffice.org-hyphenation-uk'
Package 'openoffice.org-calc' is not installed, so not removed
Package 'mozilla-openoffice.org' is not installed, so not removed
Package 'openoffice.org-kde' is not installed, so not removed
Note, selecting 'ming-fonts-opensymbol' instead of 'libming-fonts-openoffice'
Note, selecting 'myspell-fr-gut' instead of 'openoffice.org-spellcheck-fr-fr'
Note, selecting 'myspell-tl' instead of 'openoffice.org-spellcheck-tl'
Package 'openoffice.org-dmaths' is not installed, so not removed
Note, selecting 'openoffice-debian-menus' instead of 'openoffice-desktop-integration'
Package 'openofficeorg-desktop-integration' is not installed, so not removed
Package 'openoffice.org-debian-menus' is not installed, so not removed
Package 'openoffice.org-bundled' is not installed, so not removed
Note, selecting 'openoffice-debian-menus' instead of 'openoffice.org-unbundled'
Package 'kde-thumbnailer-openoffice' is not installed, so not removed
Package 'libopenoffice-oodoc-perl' is not installed, so not removed
Package 'openoffice.org-hyphenation-lt' is not installed, so not removed
Package 'openoffice.org-dtd-officedocument1.0' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.2.7) but it is not going to be installed
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
pd@pd-MM061:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 12 not upgraded.
20 not fully installed or removed.
Need to get 0 B/19.9 MB of archives.
After this operation, 76.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 205804 files and directories currently installed.)
Preparing to unpack .../libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb ...
Unpacking libreoffice-common (1:4.2.7-0ubuntu2) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.1-9775
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/prereg/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/program/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-icon-theme (3.10.0-0ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
pd@pd-MM061:~$ 

```

Besides this OO/ Libre issue, I still have this red sign with the Error : BrokenCount > 0 staring me in the face -

Thanks
PD

---

### Post by deadflowr on 2015-03-15
hmm, I'm not so sure it really removed anything.
Let's try a different approach to see
Post the output for
```
dpkg -l | grep openoffice | awk '{print $1,$2}'
```
and maybe again for libreoffice
```
dpkg -l | grep libreoffice | awk '{print $1,$2}'
```
Your problems with reinstalling libreoffice seem to stem from this
> dpkg: error processing archive /var/cache/apt/archives/libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.1.1-9775

But from the purge output only a couple of lines earlier is this
> Package 'openoffice.org-debian-menus' is not installed, so not removed
All around confusing.
So the above commands should show us what the current state of libreoffice packages and openoffice packages are on the system.
Perhaps they will shed some light on what's what.

---

### Post by pd5 on 2015-03-16
so here's what the result was -
```

pd@pd-MM061:~$ dpkg -l | grep openoffice | awk '{print $1,$2}'
ii openoffice-debian-menus
ii openoffice.org-hyphenation
pd@pd-MM061:~$ dpkg -l | grep libreoffice | awk '{print $1,$2}'
iU libreoffice
iU libreoffice-avmedia-backend-gstreamer
iU libreoffice-base
iU libreoffice-base-core
iU libreoffice-base-drivers
iU libreoffice-calc
iU libreoffice-core
iU libreoffice-draw
iU libreoffice-gnome
iU libreoffice-gtk
iU libreoffice-impress
iU libreoffice-java-common
iU libreoffice-math
iU libreoffice-pdfimport
iU libreoffice-report-builder-bin
iU libreoffice-sdbc-firebird
iU libreoffice-sdbc-hsqldb
ii libreoffice-style-galaxy
ii libreoffice-style-human
iU libreoffice-writer
pd@pd-MM061:~$ 

```

some of the libre files aren't removed ? and have to be before it can be reinstalled ? is this causing the error : brokencount >0 as well ? and why I seemingly can't install anything ?
Thanks

---

### Post by deadflowr on 2015-03-16
The brokecount >0 usually means there is some dependency problem, which is expected, since all the libreoffice packages cannot be fully installed while the libreoffice-common package is not installable.

So, it seems you do have 2 openoffice packages installed.
Perhaps try to remove those, one at a time.
Hopefully they will be removable without any problems.

If the openoffice packages produce no errors when you try to remove them, then try the apt-get install -f command, yet again.

If the openoffice packages produce errors when you try to remove them, then post the output.

---

### Post by pd5 on 2015-03-17
any way you would walk me through it ? I feel like I'm running in circles...at least there's only 2 still installed ?

not 100% sure what the commands are doing, but I repeated the previous page's removal codes for OO, I just keep seeing the same messages, it SEEMS.

Thank you for your patience.

---

### Post by deadflowr on 2015-03-17
Try
```
sudo apt-get purge openoffice-debian-menus
```
and 
```
sudo apt-get purge openoffice.org-hyphenation
```
do them one at a time.
Post any errors, if there are any errors.

If there are NO errors, then re-try the
```
sudo apt-get install -f
```
command again.

---

### Post by pd5 on 2015-03-17
Here are the errors from the first two codes. 
```

pd@pd-MM061:~$ sudo apt-get purge openoffice-debian-menus
[sudo] password for pd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.2.7) but it is not going to be installed
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
pd@pd-MM061:~$ sudo apt-get purge openoffice.org-hyphenation
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.2.7) but it is not going to be installed
 libreoffice-java-common : Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Thanks

---

### Post by pd5 on 2015-03-17
[http://askubuntu.com/questions/548392/trying-to-fix-broken-dependancies-libre-office](http://askubuntu.com/questions/548392/trying-to-fix-broken-dependancies-libre-office)

looks similar to my issue- they had no final resolution. I tried their recommendations as well- to no avail.

---

### Post by deadflowr on 2015-03-17
Well, I did find this thread, which is quite similar to yours.
[http://ubuntuforums.org/showthread.php?t=2248157](http://ubuntuforums.org/showthread.php?t=2248157)
Perhaps read through it to see if the approach it takes might help.

---

### Post by pd5 on 2015-03-17
DF,

I will. Thank you for looking.

So I ran through the webpage, tried their various codes and commands, but I still have these two dependencies and the error broken count message. Unable to use or download a word processor program I desperately need for graduate school - going on now.

I hate to think I need to trash this laptop just because of an error, but I haven't seen any solutions yet. I love working with linux, but it seems like PAST power users are no longer when new versions come out, but they all have opinions on the new versions, even though their methods work, their suggestions for fixes and codes are now outdated- it's extremely frustrating.

I've looked into and tried some other solutions that sounded very similar to this issue, but without other programs downloaded their fixes don't work.

Should I just try asking this same question on another website ? It seems the offerings for help/ guidance have fizzled to one : DF- Thank You, then none, it seems... ? 

Please advise.

---

### Post by pd5 on 2015-03-18
RESOLVED
my error was : 
  /var/cache/apt/archives/libreoffice-common_1%3a4.2.7-0ubuntu2_all.deb

See :
[http://ubuntuforums.org/showthread.php?t=1642173](http://ubuntuforums.org/showthread.php?t=1642173)

Thank you everyone for your help - wish some had more 'stick to it'-tiveness. Oh well, next time.

Error Code gone, Dependency errors gone, libre reinstalled. ;)

---

### Post by baidaraka on 2015-03-24
Salam

```
sudo apt-get purge openoffice* libreoffice* python3-uno
```

---

