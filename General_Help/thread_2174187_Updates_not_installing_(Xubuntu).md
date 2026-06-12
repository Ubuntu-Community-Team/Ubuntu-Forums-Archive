---
title: "Updates not installing (Xubuntu)"
date: 2013-09-13
forum: General Help
---

### Post by jogger2 on 2013-09-13
Hi guys,

Since a couple of days ago my update manager returns error messages when trying to install recent updates. 
Same goes when I try the manual ```
[FONT=courier new]sudo apt-get upgrade[/FONT]
``` .
So here's the error output:
##########################
 ```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  flashplugin-installer libx11-6 libx11-data libx11-xcb1 python-httplib2
  sessioninstaller
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
28 not fully installed or removed.
Need to get 0 B/1,047 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Setting up tzdata (2013d-0ubuntu0.12.04) ...
Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```###############################

Would be great if someone had an idea,
Cheers,
Robert

---

### Post by Kirboosy on 2013-09-13
Welcome to the forums!

I believe you have a broken package in your system. You should try running 

```
sudo apt-get install -f
```

Also
```
sudo apt-get autoremove
```

That might help remove any unneeded packages which might be causing issues.


Hope that helps!
~Caboose

---

### Post by jogger2 on 2013-09-13
thanks for helping,
ran both commands but they encountered similiar errors:
```
sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
28 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: Perl may be unconfigured (Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
Setting up tzdata (2013d-0ubuntu0.12.04) ...
Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up tex-common (2.10) ...
Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing tex-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of lmodern:
 lmodern depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing lmodern (--configure):
 dependency problems - leaving unconfigured
Setting up man-db (2.6.1-2ubuntu1) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of texlive-common:
 texlive-common depends on tex-common (>= 2.0); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-binaries:
 texlive-binaries depends on texlive-common (>= 2009); however:
  Package texlive-common is not configured yet.
 texlive-binaries depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing texlive-binaries (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-doc-base:
 texlive-doc-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-doc-base depends on texlive-common (>= 2009-1); howeverNo apport report written because MaxReports has already been reached
                                                    No apport report written because MaxReports has already been reached
                                        No apport report written because MaxReports has already been reached
                            No apport report written because MaxReports has already been reached
                No apport report written because MaxReports has already been reached
    No apport report written because MaxReports has already been reached
                                                                        No apport report written because MaxReports has already been reached
                                                            No apport report written because MaxReports has already been reached
                                                No apport report written because MaxReports has already been reached
                                    No apport report written because MaxReports has already been reached
                        No apport report written because MaxReports has already been reached
            No apport report written because MaxReports has already been reached
No apport report written because MaxReports has already been reached
                                                                    :
  Package texlive-common is not configured yet.
dpkg: error processing texlive-doc-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-base:
 texlive-base depends on texlive-doc-base (>= 2009-1); however:
  Package texlive-doc-base is not configured yet.
 texlive-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-base depends on texlive-binaries (>= 2009-10); however:
  Package texlive-binaries is not configured yet.
 texlive-base depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-base depends on texlive-base (>= 2009-1); however:
  Package texlNo apport report written because MaxReports has already been reached
  No apport report written because MaxReports has already been reached
                                                                      No apport report written because MaxReports has already been reached
                                                          No apport report written because MaxReports has already been reached
                                              No apport report written because MaxReports has already been reached
                                  ive-base is not configured yet.
 texlive-latex-base depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
 texlive-latex-base depends on texlive-binaries (>= 2009-1); however:
  Package texlive-binaries is not configured yet.
dpkg: error processing texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-generic-recommended depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
 texlive-generic-recommended depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks No apport report written because MaxReports has already been reached
      depends on texlive-generic-recommended (>= 2009-1); however:
  Package texlive-generic-recommended is not configured yet.
 texlive-pstricks depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-pstricks depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
 texlive-pstricks depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
 texlive-pstricks depends on texlive-binaries (>= 2009-1); however:
  Package texlive-binaries is not configured yet.
dpkg: error processing texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of asymptote:
 asymptote depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 asymptote depends on texlive-base-bin; however:
  Package texlive-base-bin is not installed.
  Package texlive-binaries which provides texlive-base-bin is not configured yet.
 asymptote depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 asymptote depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
dpkg: error processing asymptote (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
 texlive-latex-recommended depends on texlive-binaries (>= 2009-1); however:
  Package texlive-binaries is not configured yet.
 texlive-latex-recommended depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-xcolor:
 latex-xcolor depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
dpkg: error processing latex-xcolor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pgf:
 pgf depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 pgf depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 pgf depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
dpkg: error processing pgf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of latex-beamer:
 latex-beamer depends on pgf (>= 1.00-1); however:
  Package pgf is not configured yet.
 latex-beamer depends on latex-xcolor (>= 2.00-1); however:
  Package latex-xcolor is not configured yet.
 latex-beamer depends on texlive-latex-base; however:
  PackaNo apport report written because MaxReports has already been reached
                                                                           ge texlive-latex-base is not configured yet.
dpkg: error processing latex-beamer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of preview-latex-style:
 preview-latex-style depends on tex-common; however:
  Package tex-common is not configured yet.
dpkg: error processing preview-latex-style (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.
 prosper depends on tex-common (>= 1.10); however:
  Package tex-common is not configured yet.
dpkg: error processing prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent coNo apport report written because MaxReports has already been reached
                        nfiguration of texlive-extra-utils:
 texlive-extra-utils depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-extra-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
 texlive-extra-utils depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
 texlive-extra-utils depends on texlive-binaries (>= 2009-1); however:
  Package texlive-binaries is not configured yet.
dpkg: error processing texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-font-utils depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
 texlive-font-utils depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
 texlive-font-utils depends on texlive-binaries (>= 2009-1); however:
  Package texlive-binaries is not configured yet.
dpkg: error processing texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-base-doc depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-pictures depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not No apport report written because MaxReports has already been reached
                    configured yet.
 texlive-pictures depends on texlive-binaries (>= 2009-1); however:
  Package texlive-binaries is not configured yet.
dpkg: error processing texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on preview-latex-style; however:
  Package preview-latex-style is not configured yet.
 texlive-latex-extra depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-extra depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
 texlive-latex-extra depends on texlive-binaries (>= 2009-1); however:
  Package texlive-binaries is not configured yet.
 texlive-latex-extra depends on texlive-pictures (>= 2009-1); however:
  Package texlive-pictures is not configured yet.
 texlive-latex-extra depends on texlive-latex-base (>= 2009-1); however:
  Package texlive-latex-base is not configured yet.
dpkg: error processing texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-extra-doc depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-latex-recommended-doc depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-luatex:
 texlive-luatex depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-luatex depends on texlive-base (>= 2009-1); however:
  Package texlive-base is not configured yet.
 texlive-luatex depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-luatex (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-pictures-doc depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on tex-common (>= 2.00); however:
  Package tex-common is not configured yet.
 texlive-pstricks-doc depends on texlive-common (>= 2009-1); however:
  Package texlive-common is not configured yet.
dpkg: error processing texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 tzdata
 tex-common
 lmodern
 man-db
 texlive-common
 texlive-binaries
 texlive-doc-base
 texlive-base
 texlive-latex-base
 texlive-generic-recommended
 texlive-pstricks
 asymptote
 texlive-latex-recommended
 latex-xcolor
 pgf
 latex-beamer
 preview-latex-style
 prosper
 texlive-extra-utils
 texlive-font-utils
 texlive-latex-base-doc
 texlive-pictures
 texlive-latex-extra
 texlive-latex-extra-doc
 texlive-latex-recommended-doc
 texlive-luatex
 texlive-pictures-doc
 texlive-pstricks-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


So I thought because there's a lot of TeX related stuff, maybe I should purge TeXMaker, but that encountered errors as well :(
It really feels broken at the moment.

---

### Post by Kirboosy on 2013-09-13
The first error is perl related. I'm not sure if you are missing the right perl version or if its just not configured properly. 

The TEX could be reconfigured with the following command ```
sudo dpkg-reconfigure --force texlive-common
```


How did you try to install TeXMaker?

~Caboose
PS: Please put CODE tags around your outputs. It makes it easier to read. Thanks!

---

### Post by jogger2 on 2013-09-14
First sorry for the missing code tags :-X

I installed TeXMaker via ```
sudo apt-get install texmaker
``` It automatically installed the TeX-Live data (which I didn't expect) and I can create/edit LaTeX documents with it. However I do believe the problems startet with that. 

Now executing your suggested TeX reconfiguration gives:
```
sudo dpkg-reconfigure --force texlive-common
Can't locate loadable object for module POSIX in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/share/perl5/Debconf/Template.pm line 7
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/sbin/dpkg-reconfigure line 11.
BEGIN failed--compilation aborted at /usr/sbin/dpkg-reconfigure line 11.


```
So I tried to reinstall Perl by using ```
sudo apt-get update && sudo apt-get install perl


```
This lead to the same error output as in my second post.
I also gave this a shot: ```
sudo cpan
cpan[1]> upgrade
```
but it only yielded an error very smiliar to the one I've just posted.

Thank you very much for guiding me through this quagmire though!

---

### Post by Bucky Ball on 2013-09-14
*Thread moved to **General Help**.*

Welcome. Please note, ***Installations & Upgrades*** is

> For questions about *upgrading* and installation of your new Ubuntu OS.

Not regular update support. Cheers. ;)

---

### Post by jogger2 on 2013-09-14
Naively I assumed update = upgrade -.- Thanks for bearing with me. I guess in an Arch forum they'd have banned me right away ;)

------
Alright, I figure I need to configure Perl properly first, before taking on the TeX issue. Can anyone give me some hints how to do that?

Thanks for any help,

Robert

---

### Post by Kirboosy on 2013-09-16
Sorry it has taken me so long to respond.. I'm trying to recreate the issue on my virtual machine. However I'm not having any success on creating the issue.

---

### Post by jogger2 on 2013-09-17
I've googled around a bit more and somebody else had a similiar problem with perl. There the forum consensus was that you have to reinstall your system because of a hen-and-egg situation: Cannot uninstall Perl because Perl broken. So they said a manual recovery of Perl libraries or so might work but should be complicated. 
Therefore I've just reinstalled my system, didn't take more than an hour -- works quite well again.
Thank you very much for the kind support!


---edit:
just installed TeXlive, then TeXMaker -- everything works perfectly!

---

### Post by Kirboosy on 2013-09-18
Awesome to hear. Glad it was an easy enough fix. Lets hope that your system doesn't break for a long time.

Oh, and please mark the thread as "Solved"

Thanks

---

