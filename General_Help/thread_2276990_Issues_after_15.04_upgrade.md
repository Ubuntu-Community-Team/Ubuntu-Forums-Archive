---
title: "Issues after 15.04 upgrade"
date: 2015-05-06
forum: General Help
---

### Post by Phil_Brown on 2015-05-06
I am currently unable to install any new packages due to the an error after installing 15.04.

If I run apt-get update I get the following message back;

```
21 not fully installed or removed.
Need to get 0 B/46.2 kB of archives.
After this operation, 0 B of additional disk space will be us
```

I tick yes to fix the issue and I am then presented with the following;

I have tried a lot of things but cant seem to find a solution does any one have any ideas?

Thanks in advance

```
dpkg: error processing package python3-pkg-resources (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of python3-aptdaemon:
 python3-aptdaemon depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.

No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: error processing package python3-aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.gtk3widgets:
 python3-aptdaemon.gtk3widgets depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package python3-aptdaemon.gtk3widgets (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.

dpkg: error processing package software-properties-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apturl:
 apturl depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 apturl depends on python3-aptdaemon; however:
  No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            No apport report written because MaxReports is reached already
                                                                                                                                                                          No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
                                                                                 No apport report written because MaxReports is reached already
                                                                                                                                               No apport report written because MaxReports is reached already
                                                                                                                                                                                                             No apport report written because MaxReports is reached already
                                                      No apport report written because MaxReports is reached already
                                                                                                                    No apport report written because MaxReports is reached already
                                                                                                                                                                                  No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
                                                                                         No apport report written because MaxReports is reached already
                                                                                                                                                       Package python3-aptdaemon is not configured yet.
 apturl depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.

dpkg: error processing package apturl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of aptdaemon:
 aptdaemon depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package aptdaemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-gnome:
 language-selector-gnome depends on aptdaemon (>= 0.40+bzr527); however:
  Package aptdaemon is not configured yet.
 language-selector-gnome depends on python3-aptdaemon.gtk3widgets; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.

dpkg: error processing package language-selector-gnome (--configure):
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                                                                                                                                                          No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                                                                                                 No apport report written because MaxReports is reached already
                                                                                                                                                               No apport report written because MaxReports is reached already

        dpkg: dependency problems prevent configuration of python3-chardet:
 python3-chardet depends on python3-pkg-resources; however:
  Package python3-pkg-resources is not configured yet.

dpkg: error processing package python3-chardet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-requests:
 python3-requests depends on python3-chardet; however:
  Package python3-chardet is not configured yet.

dpkg: error processing package python3-requests (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-cupshelpers:
 python3-cupshelpers depends on python3-requests; however:
  Package python3-requests is not configured yet.

dpkg: error processing package python3-cupshelpers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-center:
 software-center depends on aptdaemon (>= 0.40); however:
  Package aptdaemon is not configured yet.

dpkg: error processing package software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-common:
 system-config-printer-common depends on python3-cupshelpers; however:
  Package python3-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-aptdaemon.pkcompat:
 python3-aptdaemon.pkcompat depends on python3-aptdaemon (= 1.1.1+bzr982-0ubuntu3); however:
  Package python3-aptdaemon is not configured yet.

dpkg: error processing package python3-aptdaemon.pkcompat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-gnome:
 system-config-printer-gnome depends on system-config-printer-common (>= 1.3.11+20120807-0ubuntu7); however:
  Package system-config-printer-common is not configured yet.
 system-config-printer-gnome depends on python3-requests; however:
  Package python3-requests is not configured yet.
 system-config-printer-gnome depends on packagekit-system-interface; however:
  Package packagekit-system-interface is not installed.
  Package python3-aptdaemon.pkcompat which provides packagekit-system-interface is not configured yet.

dpkg: error processing package system-config-printer-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of system-config-printer-udev:
 system-config-printer-udev depends on python3-cupshelpers; however:
  Package python3-cupshelpers is not configured yet.

dpkg: error processing package system-config-printer-udev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python3-aptdaemon.gtk3widgets (>= 0.40) | synaptic; however:
  Package python3-aptdaemon.gtk3widgets is not configured yet.
  Package synaptic is not installed.

dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on language-selector-gnome; however:
  Package language-selector-gnome is not configured yet.
 ubuntu-desktop depends on software-center; however:
  Package software-center is not configured yet.
 ubuntu-desktop depends on software-properties-gtk; however:
  Package software-properties-gtk is not configured yet.
 ubuntu-desktop depends on system-config-printer-gnome; however:
  Package system-config-printer-gnome is not configured yet.
 ubuntu-desktop depends on ubuntu-release-upgrader-gtk; however:
  Package ubuntu-release-upgrader-gtk is not configured yet.
 ubuntu-desktop depends on update-manager; however:
  Package update-manager is not configured yet.

dpkg: error processing package ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-ubufox:
 xul-ext-ubufox depends on aptdaemon; however:
  Package aptdaemon is not configured yet.

dpkg: error processing package xul-ext-ubufox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh-import-id:
 ssh-import-id depends on python3-requests (>= 1.1.0); however:
  Package python3-requests is not configured yet.

dpkg: error processing package ssh-import-id (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-manager-gnome | update-manager (>= 1:0.165); however:
  Package update-manager-gnome is not installed.
  Package update-manager is not configured yet.
 update-notifier depends on ubuntu-release-upgrader-gtk; however:
  Package ubuntu-release-upgrader-gtk is not configured yet.

dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-pkg-resources
 python3-aptdaemon
 python3-aptdaemon.gtk3widgets
 software-properties-gtk
 apturl
 aptdaemon
 language-selector-gnome
 python3-chardet
 python3-requests
 python3-cupshelpers
 software-center
 system-config-printer-common
 python3-aptdaemon.pkcompat
 system-config-printer-gnome
 system-config-printer-udev
 update-manager
 ubuntu-release-upgrader-gtk
 ubuntu-desktop
 xul-ext-ubufox
 ssh-import-id
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by dino99 on 2015-05-06
try cleaning the archive:

> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

Please post the output of  > cat /etc/apt/sources.list

---

### Post by Phil_Brown on 2015-05-06
Hi,

Thanks for your help, I have run the above to no avail.

Here is the output.

```
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu vivid-security main restricted
deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
deb http://security.ubuntu.com/ubuntu vivid-security universe
deb-src http://security.ubuntu.com/ubuntu vivid-security universe
deb http://security.ubuntu.com/ubuntu vivid-security multiverse
deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner

# deb http://repository.spotify.com stable non-free # disabled on upgrade to utopic
# deb-src http://repository.spotify.com stable non-free


```

Thanks in advance,

---

