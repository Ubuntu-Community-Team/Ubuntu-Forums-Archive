---
title: "Synaptic install weirdness"
date: 2015-10-27
forum: General Help
---

### Post by oldrocker99 on 2015-10-27
I have installed Synaptic from the command line many times. This evening, on a new install of Ubuntu MATE 14.10, I got this:
```
oldrocker99@oldrocker99-MS-7693:~$ sudo apt-get install synaptic
[sudo] password for oldrocker99: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  docbook-xml libapt-inst1.5 libapt-pkg4.12 libept1.4.12 librarian0 libxapian22 rarian-compat sgml-data
Suggested packages:
  docbook docbook-dsssl docbook-xsl docbook-defguide xapian-tools perlsgml w3-recs opensp libxml2-utils dwww menu
  deborphan apt-xapian-index tasksel
The following packages will be REMOVED:
  apport apport-gtk apt apt-transport-https apt-utils aptdaemon apturl apturl-common command-not-found
  flashplugin-installer gdebi gdebi-core language-selector-common language-selector-gnome libapt-inst1.7 libapt-pkg4.16
  python3-apport python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat
  python3-commandnotfound python3-distupgrade python3-software-properties python3-update-manager sessioninstaller
  software-properties-common software-properties-gtk system-config-printer-gnome ttf-mscorefonts-installer
  ubuntu-drivers-common ubuntu-mate-core ubuntu-mate-desktop ubuntu-mate-welcome ubuntu-minimal
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-standard unattended-upgrades update-manager
  update-manager-core update-notifier update-notifier-common
The following NEW packages will be installed:
  docbook-xml libapt-inst1.5 libapt-pkg4.12 libept1.4.12 librarian0 libxapian22 rarian-compat sgml-data synaptic
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libapt-pkg4.16 (due to apt)
0 upgraded, 9 newly installed, 43 to remove and 0 not upgraded.
Need to get 3,188 kB of archives.
After this operation, 4,383 kB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
```

Yes, I'd say that it is potentially harmful. Why are so many files to be removed (never before) this time?

Has this happened to anyone else?

---

### Post by claracc on 2015-10-27
Ubuntu 14.10 has reached its end of life support last July. I recommend you to update to a supported ubuntu: 12.04, 14.04, 15.04, 15.10.

Perhaps the end of life of 14.10 is causing the removing of such packages.

---

### Post by oldrocker99 on 2015-10-27
Oops. I meant **15**.10 beta. It was late...


Still wondering WTF is going on; why should installing Synaptic remove apt??

---

### Post by v3.xx on 2015-10-27
I have ran mate 15.10 w/synaptic for five months and have not seen or heard of this problem.  You got yourself a tough one.

---

### Post by oldrocker99 on 2015-10-27
Yes, it's a toughie. I am reinstalling, and when I opened a terminal on the live disk and tried installing Synaptic, it showed the usual reply. Hopefully, another installation will remove this weird situation.

[EDIT]The problem is resolved, and it only took three reinstalls:mad:...

---

