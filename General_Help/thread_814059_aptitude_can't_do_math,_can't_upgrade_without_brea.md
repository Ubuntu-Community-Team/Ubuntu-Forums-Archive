---
title: "aptitude can't do math, can't upgrade without breaking dependencies"
date: 2008-05-31
forum: General Help
---

### Post by Zorael on 2008-05-31
```
$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za
  openoffice.org-l10n-ja
The following packages have been kept back:
  xserver-xorg-video-intel
The following packages will be upgraded:
  openoffice.org-base-core openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-filter-binfilter
  openoffice.org-impress openoffice.org-java-common openoffice.org-kde
  openoffice.org-style-crystal openoffice.org-style-human
  openoffice.org-writer python-uno ttf-opensymbol
14 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 65.6MB of archives. After unpacking 877kB will be freed.
[b]The following packages have unmet dependencies:
  openoffice.org-l10n-en-gb: Conflicts: openoffice.org-core (>= _1:2.4.0.1_) but _1:2.4.1~rc1-1ubuntu1_ is to be installed.
  openoffice.org-l10n-en-za: Conflicts: openoffice.org-core (>= _1:2.4.0.1_) but _1:2.4.1~rc1-1ubuntu1_ is to be installed.
  openoffice.org-l10n-ja: Conflicts: openoffice.org-core (>= _1:2.4.0.1_) but _1:2.4.1~rc1-1ubuntu1_ is to be installed.[/b]
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
kubuntu-desktop
openoffice.org-calc
openoffice.org-writer

Keep the following packages at their current version:
openoffice.org-common [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-core [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-draw [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-filter-binfilter [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-impress [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-kde [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-style-crystal [1:2.4.0-3ubuntu6 (hardy, now)]
openoffice.org-style-human [1:2.4.0-3ubuntu6 (hardy, now)]
python-uno [1:2.4.0-3ubuntu6 (hardy, now)]

Score is 467

Accept this solution? [Y/n/q/?]
```

I'm sorry. How does that makes sense again?

:<

---

