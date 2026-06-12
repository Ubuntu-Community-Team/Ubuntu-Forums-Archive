---
title: "heimdal-kcm installation error"
date: 2013-09-10
forum: General Help
---

### Post by benpietras on 2013-09-10
E: heimdal-kcm: subprocess installed post-installation script returned error exit status 1

My system is 12.04 (64). Anyone else see this error? Complete removal - reinstallation.

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en_GB:en",
    LC_ALL = (unset),
    LANG = "en_GB"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97, <> line 1.
Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103, <> line 1.
Selecting previously unselected package heimdal-kcm.
(Reading database ... 664707 files and directories currently installed.)
Unpacking heimdal-kcm (from .../heimdal-kcm_1.6~git20120311.dfsg.1-2ubuntu0.1_amd64.deb) ...
Processing triggers for man-db ...
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 97.
Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale. at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 103.
Processing triggers for ureadahead ...
Setting up heimdal-kcm (1.6~git20120311.dfsg.1-2ubuntu0.1) ...
Starting Heimdal KCM: invoke-rc.d: initscript heimdal-kcm, action "start" failed.
dpkg: error processing heimdal-kcm (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
 Errors were encountered while processing:
 heimdal-kcm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up heimdal-kcm (1.6~git20120311.dfsg.1-2ubuntu0.1) ...
Starting Heimdal KCM: invoke-rc.d: initscript heimdal-kcm, action "start" failed.
dpkg: error processing heimdal-kcm (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 heimdal-kcm

---

