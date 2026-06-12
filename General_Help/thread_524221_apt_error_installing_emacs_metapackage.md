---
title: "apt error installing emacs metapackage"
date: 2007-08-12
forum: General Help
---

### Post by kyleolivo on 2007-08-12
I tried installing emacs using the "emacs" metapackage in apt and received an error regarding the package emacsen-common. Details below:

> $ sudo apt-get install emacs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emacs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
debconf: Perl may be unconfigured (Can't locate auto/DynaLoader/dl_findfile.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/DynaLoader.pm line 189
Compilation failed in require at /usr/lib/perl/5.8/IO/Handle.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/Handle.pm line 9.
Compilation failed in require at /usr/lib/perl/5.8/IO/Seekable.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/Seekable.pm line 9.
Compilation failed in require at /usr/lib/perl/5.8/IO/File.pm line 11.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/File.pm line 11.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
Setting up emacsen-common (1.4.17) ...
Can't locate auto/DynaLoader/dl_findfile.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/DynaLoader.pm line 189
Compilation failed in require at /usr/lib/emacsen-common/generate-install-list line 27.
BEGIN failed--compilation aborted at /usr/lib/emacsen-common/generate-install-list line 27.
Compilation failed in require at /usr/lib/emacsen-common/emacs-package-install line 18.
dpkg: error processing emacsen-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of emacs21-common:
 emacs21-common depends on emacsen-common (>= 1.4.10); however:
  Package emacsen-common is not configured yet.
dpkg: error processing emacs21-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs21-bin-common:
 emacs21-bin-common depends on emacs21-common (= 21.4a+1-2ubuntu1); however:
  Package emacs21-common is not configured yet.
dpkg: error processing emacs21-bin-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs21:
 emacs21 depends on emacs21-bin-common (= 21.4a+1-2ubuntu1); however:
  Package emacs21-bin-common is not configured yet.
dpkg: error processing emacs21 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of emacs:
 emacs depends on emacs21 | emacs21-nox; however:
  Package emacs21 is not configured yet.
  Package emacs21-nox is not installed.
dpkg: error processing emacs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 emacsen-common
 emacs21-common
 emacs21-bin-common
 emacs21
 emacs
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ 

The error seems to indicate an issue with perl. At this point I just wanted to remove emacs, but encountered another issue:

> $ sudo apt-get remove emacsen-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  emacs21 emacs21-bin-common emacs21-common emacsen-common
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 41.5MB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Can't locate auto/DynaLoader/dl_findfile.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/DynaLoader.pm line 189
Compilation failed in require at /usr/lib/perl/5.8/IO/Handle.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/Handle.pm line 9.
Compilation failed in require at /usr/lib/perl/5.8/IO/Seekable.pm line 9.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/Seekable.pm line 9.
Compilation failed in require at /usr/lib/perl/5.8/IO/File.pm line 11.
BEGIN failed--compilation aborted at /usr/lib/perl/5.8/IO/File.pm line 11.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 110898 files and directories currently installed.)
Removing emacs21 ...
Removing emacs21-bin-common ...
Removing emacs21-common ...
Removing emacsen-common ...
Can't locate auto/DynaLoader/dl_findfile.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/DynaLoader.pm line 189
Compilation failed in require at /usr/lib/emacsen-common/generate-install-list line 27.
BEGIN failed--compilation aborted at /usr/lib/emacsen-common/generate-install-list line 27.
Compilation failed in require at /usr/lib/emacsen-common/emacs-package-remove line 18.
dpkg: error processing emacsen-common (--remove):
 subprocess pre-removal script returned error exit status 2
Can't locate auto/DynaLoader/dl_findfile.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/lib/perl/5.8/DynaLoader.pm line 189
Compilation failed in require at /usr/lib/emacsen-common/generate-install-list line 27.
BEGIN failed--compilation aborted at /usr/lib/emacsen-common/generate-install-list line 27.
Compilation failed in require at /usr/lib/emacsen-common/emacs-package-install line 18.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 emacsen-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

The emacsen-common package will not uninstall. Does anyone have any ideas on the best way to force this package to remove itself, or perhaps how to fix the original perl issue so that this package will install correctly? Thanks.

---

