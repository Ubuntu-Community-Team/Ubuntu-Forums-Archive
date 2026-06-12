---
title: "Dependency issue: New software cannot be installed"
date: 2013-12-20
forum: General Help
---

### Post by rufuslucky on 2013-12-20
When I open ubuntu software center I get a warning box that tells me 'New software cannot be installed because there is a problem with software already installed. Do you want to repair this problem now?" This all stems from the fact that I removed libreoffice with sudo-apt get purge because it wouldn't render word documents correctly. I am attempting to replace it with open-office because that program never had an issue with word documents. I've been having some difficulty finding a source online that will help me do that so I decided to reinstall libreoffice so that I would at least have one word processor even if it wasn't a good word processor. When I did that I decided to go strait to the source and added a repository that I thought was for the most recent version of libreoffice and I installed via terminal. It apparently wasn't the right repository because libreoffice did not install and now I have dependancy issues that block me from using ubuntu software center. When I hit "repair" option in the afore mentioned warning box the repair fails and spits out this dialogue.
```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
rmdir: failed to remove /var/lib/libreoffice/share/prereg/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/share/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/program/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
Error in function: 
dpkg: dependency problems prevent configuration of libreoffice-java-common:
 libreoffice-java-common depends on libreoffice-common; however:
  Package libreoffice-common is not installed.
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
rmdir: failed to remove /var/lib/libreoffice/share/prereg/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/share/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/program/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
Error in function: 
dpkg: dependency problems prevent configuration of libreoffice-java-common:
 libreoffice-java-common depends on libreoffice-common; however:
  Package libreoffice-common is not installed.

dpkg: error processing libreoffice-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-java-common (>= 1:4.1.3~); however:
  Package libreoffice-java-common is not configured yet.

dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.

dpkg: error processing libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:4.1.3); however:
  Package libreoffice-common is not installed.

dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:4.1.3-0ubuntu1); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.1.3-0ubuntu1); howeve
dpkg: error processing libreoffice-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-java-common (>= 1:4.1.3~); however:
  Package libreoffice-java-common is not configured yet.

dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.

dpkg: error processing libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:4.1.3); however:
  Package libreoffice-common is not installed.

dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:4.1.3-0ubuntu1); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.1.3-0ubuntu1); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
```

I figured I'd try purging libreoffice again, you know just for shits and giggles, and this is what I got.
```
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-lightproof-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-unbundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-4.1' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-templates' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-js' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pt-br' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-kk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-kk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-librelogo' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-or' for regex 'libreoffice*'
Note, selecting 'libreoffice.org-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-bsh' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-rw' for regex 'libreoffice*'
Note, selecting 'unity-scope-asklibreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sv' for regex 'libreoffice*'
Package 'libreoffice-gcj' is not installed, so not removed
Package 'libreoffice-filter-mobiledev' is not installed, so not removed
Package 'libreoffice-l10n-3.5' is not installed, so not removed
Package 'libreoffice-l10n-3.6' is not installed, so not removed
Package 'libreoffice-style-andromeda' is not installed, so not removed
Package 'zotero-libreoffice-integration' is not installed, so not removed
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Package 'libreoffice-filter-binfilter' is not installed, so not removed
Package 'libreoffice-unbundled' is not installed, so not removed
Package 'libreoffice-evolution' is not installed, so not removed
Package 'libreoffice-kab' is not installed, so not removed
Note, selecting 'browser-plugin-libreoffice' instead of 'mozilla-libreoffice'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Package 'libreoffice-grammarcheck-af' is not installed, so not removed
Package 'libreoffice-help-af' is not installed, so not removed
Package 'libreoffice-grammarcheck-ar' is not installed, so not removed
Package 'libreoffice-help-ar' is not installed, so not removed
Package 'libreoffice-grammarcheck-as' is not installed, so not removed
Package 'libreoffice-help-as' is not installed, so not removed
Package 'libreoffice-grammarcheck-ast' is not installed, so not removed
Package 'libreoffice-help-ast' is not installed, so not removed
Package 'libreoffice-grammarcheck-be' is not installed, so not removed
Package 'libreoffice-help-be' is not installed, so not removed
Package 'libreoffice-grammarcheck-bg' is not installed, so not removed
Package 'libreoffice-help-bg' is not installed, so not removed
Package 'libreoffice-grammarcheck-bn' is not installed, so not removed
Package 'libreoffice-help-bn' is not installed, so not removed
Package 'libreoffice-grammarcheck-br' is not installed, so not removed
Package 'libreoffice-help-br' is not installed, so not removed
Package 'libreoffice-grammarcheck-bs' is not installed, so not removed
Package 'libreoffice-help-bs' is not installed, so not removed
Package 'libreoffice-grammarcheck-ca' is not installed, so not removed
Package 'libreoffice-grammarcheck-cs' is not installed, so not removed
Package 'libreoffice-grammarcheck-cy' is not installed, so not removed
Package 'libreoffice-help-cy' is not installed, so not removed
Package 'libreoffice-grammarcheck-da' is not installed, so not removed
Package 'libreoffice-grammarcheck-de' is not installed, so not removed
Package 'libreoffice-grammarcheck-dz' is not installed, so not removed
Package 'libreoffice-grammarcheck-el' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-gb'
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-za'
Package 'libreoffice-help-en-za' is not installed, so not removed
Package 'libreoffice-grammarcheck-eo' is not installed, so not removed
Package 'libreoffice-help-eo' is not installed, so not removed
Package 'libreoffice-grammarcheck-es' is not installed, so not removed
Package 'libreoffice-grammarcheck-et' is not installed, so not removed
Package 'libreoffice-grammarcheck-eu' is not installed, so not removed
Package 'libreoffice-grammarcheck-fa' is not installed, so not removed
Package 'libreoffice-help-fa' is not installed, so not removed
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Package 'libreoffice-grammarcheck-fi' is not installed, so not removed
Package 'libreoffice-grammarcheck-fr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ga' is not installed, so not removed
Package 'libreoffice-help-ga' is not installed, so not removed
Package 'libreoffice-grammarcheck-gl' is not installed, so not removed
Package 'libreoffice-grammarcheck-gu' is not installed, so not removed
Package 'libreoffice-help-gu' is not installed, so not removed
Package 'libreoffice-grammarcheck-he' is not installed, so not removed
Package 'libreoffice-help-he' is not installed, so not removed
Package 'libreoffice-grammarcheck-hi' is not installed, so not removed
Package 'libreoffice-grammarcheck-hr' is not installed, so not removed
Package 'libreoffice-help-hr' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-hu' instead of 'libreoffice-grammarcheck-hu'
Package 'libreoffice-grammarcheck-id' is not installed, so not removed
Package 'libreoffice-help-id' is not installed, so not removed
Package 'libreoffice-grammarcheck-is' is not installed, so not removed
Package 'libreoffice-help-is' is not installed, so not removed
Package 'libreoffice-grammarcheck-it' is not installed, so not removed
Package 'libreoffice-grammarcheck-ja' is not installed, so not removed
Package 'libreoffice-grammarcheck-ka' is not installed, so not removed
Package 'libreoffice-help-ka' is not installed, so not removed
Package 'libreoffice-grammarcheck-kk' is not installed, so not removed
Package 'libreoffice-help-kk' is not installed, so not removed
Package 'libreoffice-grammarcheck-km' is not installed, so not removed
Package 'libreoffice-grammarcheck-ko' is not installed, so not removed
Package 'libreoffice-grammarcheck-ku' is not installed, so not removed
Package 'libreoffice-help-ku' is not installed, so not removed
Package 'libreoffice-grammarcheck-lt' is not installed, so not removed
Package 'libreoffice-help-lt' is not installed, so not removed
Package 'libreoffice-grammarcheck-lv' is not installed, so not removed
Package 'libreoffice-help-lv' is not installed, so not removed
Package 'libreoffice-grammarcheck-mk' is not installed, so not removed
Package 'libreoffice-help-mk' is not installed, so not removed
Package 'libreoffice-grammarcheck-ml' is not installed, so not removed
Package 'libreoffice-help-ml' is not installed, so not removed
Package 'libreoffice-grammarcheck-mn' is not installed, so not removed
Package 'libreoffice-help-mn' is not installed, so not removed
Package 'libreoffice-grammarcheck-mr' is not installed, so not removed
Package 'libreoffice-help-mr' is not installed, so not removed
Package 'libreoffice-grammarcheck-nb' is not installed, so not removed
Package 'libreoffice-help-nb' is not installed, so not removed
Package 'libreoffice-grammarcheck-ne' is not installed, so not removed
Package 'libreoffice-help-ne' is not installed, so not removed
Package 'libreoffice-grammarcheck-nl' is not installed, so not removed
Package 'libreoffice-grammarcheck-nn' is not installed, so not removed
Package 'libreoffice-help-nn' is not installed, so not removed
Package 'libreoffice-grammarcheck-nr' is not installed, so not removed
Package 'libreoffice-help-nr' is not installed, so not removed
Package 'libreoffice-grammarcheck-nso' is not installed, so not removed
Package 'libreoffice-help-nso' is not installed, so not removed
Package 'libreoffice-grammarcheck-oc' is not installed, so not removed
Package 'libreoffice-help-oc' is not installed, so not removed
Package 'libreoffice-grammarcheck-om' is not installed, so not removed
Package 'libreoffice-grammarcheck-or' is not installed, so not removed
Package 'libreoffice-help-or' is not installed, so not removed
Package 'libreoffice-grammarcheck-pa-in' is not installed, so not removed
Package 'libreoffice-help-pa-in' is not installed, so not removed
Package 'libreoffice-grammarcheck-pl' is not installed, so not removed
Package 'libreoffice-grammarcheck-pt' is not installed, so not removed
Package 'libreoffice-grammarcheck-pt-br' is not installed, so not removed
Package 'libreoffice-grammarcheck-ro' is not installed, so not removed
Package 'libreoffice-help-ro' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-ru-ru' instead of 'libreoffice-grammarcheck-ru'
Package 'libreoffice-grammarcheck-rw' is not installed, so not removed
Package 'libreoffice-help-rw' is not installed, so not removed
Package 'libreoffice-grammarcheck-si' is not installed, so not removed
Package 'libreoffice-help-si' is not installed, so not removed
Package 'libreoffice-grammarcheck-sk' is not installed, so not removed
Package 'libreoffice-grammarcheck-sl' is not installed, so not removed
Package 'libreoffice-grammarcheck-sr' is not installed, so not removed
Package 'libreoffice-help-sr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ss' is not installed, so not removed
Package 'libreoffice-help-ss' is not installed, so not removed
Package 'libreoffice-grammarcheck-st' is not installed, so not removed
Package 'libreoffice-help-st' is not installed, so not removed
Package 'libreoffice-grammarcheck-sv' is not installed, so not removed
Package 'libreoffice-grammarcheck-ta' is not installed, so not removed
Package 'libreoffice-help-ta' is not installed, so not removed
Package 'libreoffice-grammarcheck-te' is not installed, so not removed
Package 'libreoffice-help-te' is not installed, so not removed
Package 'libreoffice-grammarcheck-tg' is not installed, so not removed
Package 'libreoffice-help-tg' is not installed, so not removed
Package 'libreoffice-grammarcheck-th' is not installed, so not removed
Package 'libreoffice-help-th' is not installed, so not removed
Package 'libreoffice-grammarcheck-tn' is not installed, so not removed
Package 'libreoffice-help-tn' is not installed, so not removed
Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-spellcheck-tr'
Package 'libreoffice-grammarcheck-tr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ts' is not installed, so not removed
Package 'libreoffice-help-ts' is not installed, so not removed
Package 'libreoffice-grammarcheck-ug' is not installed, so not removed
Package 'libreoffice-help-ug' is not installed, so not removed
Package 'libreoffice-grammarcheck-uk' is not installed, so not removed
Package 'libreoffice-help-uk' is not installed, so not removed
Package 'libreoffice-grammarcheck-uz' is not installed, so not removed
Package 'libreoffice-help-uz' is not installed, so not removed
Package 'libreoffice-grammarcheck-ve' is not installed, so not removed
Package 'libreoffice-help-ve' is not installed, so not removed
Package 'libreoffice-grammarcheck-vi' is not installed, so not removed
Package 'libreoffice-grammarcheck-xh' is not installed, so not removed
Package 'libreoffice-help-xh' is not installed, so not removed
Package 'libreoffice-grammarcheck-zh-cn' is not installed, so not removed
Package 'libreoffice-grammarcheck-zh-tw' is not installed, so not removed
Package 'libreoffice-grammarcheck-zu' is not installed, so not removed
Package 'libreoffice-help-zu' is not installed, so not removed
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'unity-scope-home' instead of 'unity-scope-asklibreoffice'
Package 'libreoffice.org-calc' is not installed, so not removed
Package 'libreoffice.org-writer' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-us'
Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'
Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-hyphenation-tr'
Package 'libreoffice-nlpsolver' is not installed, so not removed
Package 'libreoffice-voikko' is not installed, so not removed
Package 'libreoffice-dmaths' is not installed, so not removed
Package 'libreoffice-lightproof-en' is not installed, so not removed
Package 'libreoffice-lightproof-hu' is not installed, so not removed
Package 'libreoffice-lightproof-ru-ru' is not installed, so not removed
Package 'libreoffice-templates' is not installed, so not removed
Package 'libreoffice-writer2latex' is not installed, so not removed
Package 'libreoffice-writer2xhtml' is not installed, so not removed
Package 'libreoffice-zemberek' is not installed, so not removed
Package 'openclipart-libreoffice' is not installed, so not removed
Package 'openclipart2-libreoffice' is not installed, so not removed
Package 'browser-plugin-libreoffice' is not installed, so not removed
Package 'libreoffice-emailmerge' is not installed, so not removed
Package 'libreoffice-gtk3' is not installed, so not removed
Package 'libreoffice-kde' is not installed, so not removed
Package 'libreoffice-librelogo' is not installed, so not removed
Package 'libreoffice-mysql-connector' is not installed, so not removed
Package 'libreoffice-presenter-console' is not installed, so not removed
Package 'libreoffice-report-builder' is not installed, so not removed
Package 'libreoffice-script-provider-bsh' is not installed, so not removed
Package 'libreoffice-script-provider-js' is not installed, so not removed
Package 'libreoffice-script-provider-python' is not installed, so not removed
Package 'libreoffice-sdbc-postgresql' is not installed, so not removed
Package 'libreoffice-style-crystal' is not installed, so not removed
Package 'libreoffice-style-hicontrast' is not installed, so not removed
Package 'libreoffice-style-oxygen' is not installed, so not removed
Package 'libreoffice-subsequentcheckbase' is not installed, so not removed
Package 'libreoffice-wiki-publisher' is not installed, so not removed
Package 'libreoffice-common' is not installed, so not removed
Package 'libreoffice-dbg' is not installed, so not removed
Package 'libreoffice-dev' is not installed, so not removed
Package 'libreoffice-dev-doc' is not installed, so not removed
Package 'libreoffice-help-ca' is not installed, so not removed
Package 'libreoffice-help-cs' is not installed, so not removed
Package 'libreoffice-help-da' is not installed, so not removed
Package 'libreoffice-help-de' is not installed, so not removed
Package 'libreoffice-help-dz' is not installed, so not removed
Package 'libreoffice-help-el' is not installed, so not removed
Package 'libreoffice-help-en-gb' is not installed, so not removed
Package 'libreoffice-help-en-us' is not installed, so not removed
Package 'libreoffice-help-es' is not installed, so not removed
Package 'libreoffice-help-et' is not installed, so not removed
Package 'libreoffice-help-eu' is not installed, so not removed
Package 'libreoffice-help-fi' is not installed, so not removed
Package 'libreoffice-help-fr' is not installed, so not removed
Package 'libreoffice-help-gl' is not installed, so not removed
Package 'libreoffice-help-hi' is not installed, so not removed
Package 'libreoffice-help-hu' is not installed, so not removed
Package 'libreoffice-help-it' is not installed, so not removed
Package 'libreoffice-help-ja' is not installed, so not removed
Package 'libreoffice-help-km' is not installed, so not removed
Package 'libreoffice-help-ko' is not installed, so not removed
Package 'libreoffice-help-nl' is not installed, so not removed
Package 'libreoffice-help-om' is not installed, so not removed
Package 'libreoffice-help-pl' is not installed, so not removed
Package 'libreoffice-help-pt' is not installed, so not removed
Package 'libreoffice-help-pt-br' is not installed, so not removed
Package 'libreoffice-help-ru' is not installed, so not removed
Package 'libreoffice-help-sk' is not installed, so not removed
Package 'libreoffice-help-sl' is not installed, so not removed
Package 'libreoffice-help-sv' is not installed, so not removed
Package 'libreoffice-help-tr' is not installed, so not removed
Package 'libreoffice-help-vi' is not installed, so not removed
Package 'libreoffice-help-zh-cn' is not installed, so not removed
Package 'libreoffice-help-zh-tw' is not installed, so not removed
Package 'libreoffice-l10n-af' is not installed, so not removed
Package 'libreoffice-l10n-ar' is not installed, so not removed
Package 'libreoffice-l10n-as' is not installed, so not removed
Package 'libreoffice-l10n-ast' is not installed, so not removed
Package 'libreoffice-l10n-be' is not installed, so not removed
Package 'libreoffice-l10n-bg' is not installed, so not removed
Package 'libreoffice-l10n-bn' is not installed, so not removed
Package 'libreoffice-l10n-br' is not installed, so not removed
Package 'libreoffice-l10n-bs' is not installed, so not removed
Package 'libreoffice-l10n-ca' is not installed, so not removed
Package 'libreoffice-l10n-cs' is not installed, so not removed
Package 'libreoffice-l10n-cy' is not installed, so not removed
Package 'libreoffice-l10n-da' is not installed, so not removed
Package 'libreoffice-l10n-de' is not installed, so not removed
Package 'libreoffice-l10n-dz' is not installed, so not removed
Package 'libreoffice-l10n-el' is not installed, so not removed
Package 'libreoffice-l10n-en-gb' is not installed, so not removed
Package 'libreoffice-l10n-en-za' is not installed, so not removed
Package 'libreoffice-l10n-eo' is not installed, so not removed
Package 'libreoffice-l10n-es' is not installed, so not removed
Package 'libreoffice-l10n-et' is not installed, so not removed
Package 'libreoffice-l10n-eu' is not installed, so not removed
Package 'libreoffice-l10n-fa' is not installed, so not removed
Package 'libreoffice-l10n-fi' is not installed, so not removed
Package 'libreoffice-l10n-fr' is not installed, so not removed
Package 'libreoffice-l10n-ga' is not installed, so not removed
Package 'libreoffice-l10n-gl' is not installed, so not removed
Package 'libreoffice-l10n-gu' is not installed, so not removed
Package 'libreoffice-l10n-he' is not installed, so not removed
Package 'libreoffice-l10n-hi' is not installed, so not removed
Package 'libreoffice-l10n-hr' is not installed, so not removed
Package 'libreoffice-l10n-hu' is not installed, so not removed
Package 'libreoffice-l10n-id' is not installed, so not removed
Package 'libreoffice-l10n-in' is not installed, so not removed
Package 'libreoffice-l10n-is' is not installed, so not removed
Package 'libreoffice-l10n-it' is not installed, so not removed
Package 'libreoffice-l10n-ja' is not installed, so not removed
Package 'libreoffice-l10n-ka' is not installed, so not removed
Package 'libreoffice-l10n-kk' is not installed, so not removed
Package 'libreoffice-l10n-km' is not installed, so not removed
Package 'libreoffice-l10n-ko' is not installed, so not removed
Package 'libreoffice-l10n-ku' is not installed, so not removed
Package 'libreoffice-l10n-lt' is not installed, so not removed
Package 'libreoffice-l10n-lv' is not installed, so not removed
Package 'libreoffice-l10n-mk' is not installed, so not removed
Package 'libreoffice-l10n-ml' is not installed, so not removed
Package 'libreoffice-l10n-mn' is not installed, so not removed
Package 'libreoffice-l10n-mr' is not installed, so not removed
Package 'libreoffice-l10n-nb' is not installed, so not removed
Package 'libreoffice-l10n-ne' is not installed, so not removed
Package 'libreoffice-l10n-nl' is not installed, so not removed
Package 'libreoffice-l10n-nn' is not installed, so not removed
Package 'libreoffice-l10n-nr' is not installed, so not removed
Package 'libreoffice-l10n-nso' is not installed, so not removed
Package 'libreoffice-l10n-oc' is not installed, so not removed
Package 'libreoffice-l10n-om' is not installed, so not removed
Package 'libreoffice-l10n-or' is not installed, so not removed
Package 'libreoffice-l10n-pa-in' is not installed, so not removed
Package 'libreoffice-l10n-pl' is not installed, so not removed
Package 'libreoffice-l10n-pt' is not installed, so not removed
Package 'libreoffice-l10n-pt-br' is not installed, so not removed
Package 'libreoffice-l10n-ro' is not installed, so not removed
Package 'libreoffice-l10n-ru' is not installed, so not removed
Package 'libreoffice-l10n-rw' is not installed, so not removed
Package 'libreoffice-l10n-si' is not installed, so not removed
Package 'libreoffice-l10n-sk' is not installed, so not removed
Package 'libreoffice-l10n-sl' is not installed, so not removed
Package 'libreoffice-l10n-sr' is not installed, so not removed
Package 'libreoffice-l10n-ss' is not installed, so not removed
Package 'libreoffice-l10n-st' is not installed, so not removed
Package 'libreoffice-l10n-sv' is not installed, so not removed
Package 'libreoffice-l10n-ta' is not installed, so not removed
Package 'libreoffice-l10n-te' is not installed, so not removed
Package 'libreoffice-l10n-tg' is not installed, so not removed
Package 'libreoffice-l10n-th' is not installed, so not removed
Package 'libreoffice-l10n-tn' is not installed, so not removed
Package 'libreoffice-l10n-tr' is not installed, so not removed
Package 'libreoffice-l10n-ts' is not installed, so not removed
Package 'libreoffice-l10n-ug' is not installed, so not removed
Package 'libreoffice-l10n-uk' is not installed, so not removed
Package 'libreoffice-l10n-uz' is not installed, so not removed
Package 'libreoffice-l10n-ve' is not installed, so not removed
Package 'libreoffice-l10n-vi' is not installed, so not removed
Package 'libreoffice-l10n-xh' is not installed, so not removed
Package 'libreoffice-l10n-za' is not installed, so not removed
Package 'libreoffice-l10n-zh-cn' is not installed, so not removed
Package 'libreoffice-l10n-zh-tw' is not installed, so not removed
Package 'libreoffice-l10n-zu' is not installed, so not removed
Package 'libreoffice-officebean' is not installed, so not removed
Package 'libreoffice-ogltrans' is not installed, so not removed
Package 'libreoffice-presentation-minimizer' is not installed, so not removed
Package 'libreoffice-style-tango' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python3-uno : Depends: libreoffice-core (= 1:4.1.3-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I then decided to do as suggested and got this. 
```
rufuslucky@rufuslucky-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic
  linux-image-3.11.0-12-generic linux-image-3.8.0-32-generic
  linux-image-extra-3.11.0-12-generic linux-image-extra-3.8.0-32-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/27.0 MB of archives.
After this operation, 77.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
                                                              rmdir: failed to remove &#8216;/var/lib/libreoffice/share/prereg/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/program/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'rufuslucky@rufuslucky-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic
  linux-image-3.11.0-12-generic linux-image-3.8.0-32-generic
  linux-image-extra-3.11.0-12-generic linux-image-extra-3.8.0-32-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/27.0 MB of archives.
After this operation, 77.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
                                                              rmdir: failed to remove &#8216;/var/lib/libreoffice/share/prereg/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/program/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rufuslucky@rufuslucky-desktop:~$ 
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rufuslucky@rufuslucky-desktop:~$ 
```

Obviously I know just enough to be dangerous, but not enough to clean up after myself. Can somebody help solve these dependency issues. Somebody who can explain things as if talking to a complete idiot. Thanks.

---

### Post by tgalati4 on 2013-12-20
I would reinstall LibreOffice.  It's tightly tied to Ubuntu, so removing it can cause some issues.  I believe you can install OpenOffice alongside LibreOffice, but you will have to do some research.

```
sudo apt-get clean
sudo apt-get check
sudo apt-get install libreoffice-common
```

Install whatever other libreoffice packages are needed to get it to work properly.

---

### Post by rufuslucky on 2013-12-20
Thanks for the tip. It didn't work though. 
```
rufuslucky@rufuslucky-desktop:~$ sudo apt-get clean
[sudo] password for rufuslucky: 
rufuslucky@rufuslucky-desktop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-core : Depends: libreoffice-common (> 1:4.1.3) but it is not installed
 libreoffice-java-common : Depends: libreoffice-common but it is not installed
E: Unmet dependencies. Try using -f.
rufuslucky@rufuslucky-desktop:~$ sudo apt-get install libreoffice-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic
  linux-image-3.11.0-12-generic linux-image-3.8.0-32-generic
  linux-image-extra-3.11.0-12-generic linux-image-extra-3.8.0-32-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast libreoffice-style-oxygen
  libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 27.0 MB of archives.
After this operation, 77.2 MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) saucy-updates/main libreoffice-common all 1:4.1.3-0ubuntu1 [27.0 MB]
Fetched 27.0 MB in 10s (2,637 kB/s)                                                   
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
                                                              rmdir: failed to remove &#8216;/var/lib/libreoffice/share/prereg/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/share/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice/program/&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
rmdir: failed to remove &#8216;/var/lib/libreoffice&#8217;: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I think what the problem seems to be is that I tryed to install open office and it shares certain dependancies with libre office which is screwing up the installation of libre office. For instance when I tried to install oppenoffice it created a broken link in /usr/bin called soffice. I can't seem to git rid of or modify the damn thing. I don't know enough command line to get rid of it that way and don't recall how to get root permissions to trash the thing via gui
.

---

### Post by rufuslucky on 2013-12-20
There are also some other broken links in the open office package I downloaded that I don't seem to have access to.

---

### Post by rufuslucky on 2013-12-20
I've made some progress using synaptic package manager to remove the broken libreoffice packages, but I haven't been able to reinstall due to residual faulty pathways left over from the installation attemp of openoffice.

---

### Post by Toz on 2013-12-20
@rufuslucky, I've added code tags to your terminal results to make them easier to read. In the future, when you paste code or terminal results, please paste them inbetween **[noparse]```
 
```[/noparse]** tags for better readability. Thanks.

More info about code tags [here.]("http://ubuntuforums.org/misc.php?do=bbcode")

---

### Post by tgalati4 on 2013-12-20
soffice points to:


tgalati4@tpad-Gloria7 /usr/bin $ ls -la soffice
lrwxrwxrwx 1 root root 33 2010-06-08 12:40 soffice -> ../lib/openoffice/program/soffice

You can delete it:

```
sudo rm /usr/bin/soffice
```

Also remove the *.deb file which is either broken or the incorrect version:

```
sudo rm /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
```

Now remove the crud:

```
sudo apt-get autoremove
```

Now install libreoffice-core:

```
sudo apt-get install libreoffice
```

Take note and only post the openoffice conflicts.  You want to fix things before you break them again.

---

### Post by exl0 on 2014-03-20
Hi rufslucky,


I recently did exactly what you did, namely trying to install and remove libreoffice and openoffice and got the dependencies tangled. Now I can't install any new software package either using apt-get or the Ubuntu software center. I tired all the suggestions that I can find online, (i.e. [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install -f [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]) [/FONT][/COLOR]but none worked. Worse, I don't have the Synaptic Package Manager installed, so I am totally stuck.


Wonder if anybody can give me some advice. Much appreciated.



> **rufuslucky said:**
> When I open ubuntu software center I get a warning box that tells me 'New software cannot be installed because there is a problem with software already installed. Do you want to repair this problem now?" This all stems from the fact that I removed libreoffice with sudo-apt get purge because it wouldn't render word documents correctly. I am attempting to replace it with open-office because that program never had an issue with word documents. I've been having some difficulty finding a source online that will help me do that so I decided to reinstall libreoffice so that I would at least have one word processor even if it wasn't a good word processor. When I did that I decided to go strait to the source and added a repository that I thought was for the most recent version of libreoffice and I installed via terminal. It apparently wasn't the right repository because libreoffice did not install and now I have dependancy issues that block me from using ubuntu software center. When I hit "repair" option in the afore mentioned warning box the repair fails and spits out this dialogue.
```
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
rmdir: failed to remove /var/lib/libreoffice/share/prereg/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/share/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/program/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
Error in function: 
dpkg: dependency problems prevent configuration of libreoffice-java-common:
 libreoffice-java-common depends on libreoffice-common; however:
  Package libreoffice-common is not installed.
installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
rmdir: failed to remove /var/lib/libreoffice/share/prereg/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/share/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice/program/: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
rmdir: failed to remove /var/lib/libreoffice: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
Error in function: 
dpkg: dependency problems prevent configuration of libreoffice-java-common:
 libreoffice-java-common depends on libreoffice-common; however:
  Package libreoffice-common is not installed.

dpkg: error processing libreoffice-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-java-common (>= 1:4.1.3~); however:
  Package libreoffice-java-common is not configured yet.

dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.

dpkg: error processing libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:4.1.3); however:
  Package libreoffice-common is not installed.

dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:4.1.3-0ubuntu1); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.1.3-0ubuntu1); howeve
dpkg: error processing libreoffice-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-java-common (>= 1:4.1.3~); however:
  Package libreoffice-java-common is not configured yet.

dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:
 libreoffice-report-builder-bin depends on libreoffice-base; however:
  Package libreoffice-base is not configured yet.

dpkg: error processing libreoffice-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-core depends on libreoffice-common (>> 1:4.1.3); however:
  Package libreoffice-common is not installed.

dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:4.1.3-0ubuntu1); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.1.3-0ubuntu1); however:
  Package libreoffice-core is not configured yet.

dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
```

I figured I'd try purging libreoffice again, you know just for shits and giggles, and this is what I got.
```
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-lightproof-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-unbundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-4.1' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-templates' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-js' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pt-br' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-kk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-kk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-librelogo' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-or' for regex 'libreoffice*'
Note, selecting 'libreoffice.org-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-bsh' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-rw' for regex 'libreoffice*'
Note, selecting 'unity-scope-asklibreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-grammarcheck-sv' for regex 'libreoffice*'
Package 'libreoffice-gcj' is not installed, so not removed
Package 'libreoffice-filter-mobiledev' is not installed, so not removed
Package 'libreoffice-l10n-3.5' is not installed, so not removed
Package 'libreoffice-l10n-3.6' is not installed, so not removed
Package 'libreoffice-style-andromeda' is not installed, so not removed
Package 'zotero-libreoffice-integration' is not installed, so not removed
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Package 'libreoffice-filter-binfilter' is not installed, so not removed
Package 'libreoffice-unbundled' is not installed, so not removed
Package 'libreoffice-evolution' is not installed, so not removed
Package 'libreoffice-kab' is not installed, so not removed
Note, selecting 'browser-plugin-libreoffice' instead of 'mozilla-libreoffice'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Package 'libreoffice-grammarcheck-af' is not installed, so not removed
Package 'libreoffice-help-af' is not installed, so not removed
Package 'libreoffice-grammarcheck-ar' is not installed, so not removed
Package 'libreoffice-help-ar' is not installed, so not removed
Package 'libreoffice-grammarcheck-as' is not installed, so not removed
Package 'libreoffice-help-as' is not installed, so not removed
Package 'libreoffice-grammarcheck-ast' is not installed, so not removed
Package 'libreoffice-help-ast' is not installed, so not removed
Package 'libreoffice-grammarcheck-be' is not installed, so not removed
Package 'libreoffice-help-be' is not installed, so not removed
Package 'libreoffice-grammarcheck-bg' is not installed, so not removed
Package 'libreoffice-help-bg' is not installed, so not removed
Package 'libreoffice-grammarcheck-bn' is not installed, so not removed
Package 'libreoffice-help-bn' is not installed, so not removed
Package 'libreoffice-grammarcheck-br' is not installed, so not removed
Package 'libreoffice-help-br' is not installed, so not removed
Package 'libreoffice-grammarcheck-bs' is not installed, so not removed
Package 'libreoffice-help-bs' is not installed, so not removed
Package 'libreoffice-grammarcheck-ca' is not installed, so not removed
Package 'libreoffice-grammarcheck-cs' is not installed, so not removed
Package 'libreoffice-grammarcheck-cy' is not installed, so not removed
Package 'libreoffice-help-cy' is not installed, so not removed
Package 'libreoffice-grammarcheck-da' is not installed, so not removed
Package 'libreoffice-grammarcheck-de' is not installed, so not removed
Package 'libreoffice-grammarcheck-dz' is not installed, so not removed
Package 'libreoffice-grammarcheck-el' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-gb'
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-za'
Package 'libreoffice-help-en-za' is not installed, so not removed
Package 'libreoffice-grammarcheck-eo' is not installed, so not removed
Package 'libreoffice-help-eo' is not installed, so not removed
Package 'libreoffice-grammarcheck-es' is not installed, so not removed
Package 'libreoffice-grammarcheck-et' is not installed, so not removed
Package 'libreoffice-grammarcheck-eu' is not installed, so not removed
Package 'libreoffice-grammarcheck-fa' is not installed, so not removed
Package 'libreoffice-help-fa' is not installed, so not removed
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Package 'libreoffice-grammarcheck-fi' is not installed, so not removed
Package 'libreoffice-grammarcheck-fr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ga' is not installed, so not removed
Package 'libreoffice-help-ga' is not installed, so not removed
Package 'libreoffice-grammarcheck-gl' is not installed, so not removed
Package 'libreoffice-grammarcheck-gu' is not installed, so not removed
Package 'libreoffice-help-gu' is not installed, so not removed
Package 'libreoffice-grammarcheck-he' is not installed, so not removed
Package 'libreoffice-help-he' is not installed, so not removed
Package 'libreoffice-grammarcheck-hi' is not installed, so not removed
Package 'libreoffice-grammarcheck-hr' is not installed, so not removed
Package 'libreoffice-help-hr' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-hu' instead of 'libreoffice-grammarcheck-hu'
Package 'libreoffice-grammarcheck-id' is not installed, so not removed
Package 'libreoffice-help-id' is not installed, so not removed
Package 'libreoffice-grammarcheck-is' is not installed, so not removed
Package 'libreoffice-help-is' is not installed, so not removed
Package 'libreoffice-grammarcheck-it' is not installed, so not removed
Package 'libreoffice-grammarcheck-ja' is not installed, so not removed
Package 'libreoffice-grammarcheck-ka' is not installed, so not removed
Package 'libreoffice-help-ka' is not installed, so not removed
Package 'libreoffice-grammarcheck-kk' is not installed, so not removed
Package 'libreoffice-help-kk' is not installed, so not removed
Package 'libreoffice-grammarcheck-km' is not installed, so not removed
Package 'libreoffice-grammarcheck-ko' is not installed, so not removed
Package 'libreoffice-grammarcheck-ku' is not installed, so not removed
Package 'libreoffice-help-ku' is not installed, so not removed
Package 'libreoffice-grammarcheck-lt' is not installed, so not removed
Package 'libreoffice-help-lt' is not installed, so not removed
Package 'libreoffice-grammarcheck-lv' is not installed, so not removed
Package 'libreoffice-help-lv' is not installed, so not removed
Package 'libreoffice-grammarcheck-mk' is not installed, so not removed
Package 'libreoffice-help-mk' is not installed, so not removed
Package 'libreoffice-grammarcheck-ml' is not installed, so not removed
Package 'libreoffice-help-ml' is not installed, so not removed
Package 'libreoffice-grammarcheck-mn' is not installed, so not removed
Package 'libreoffice-help-mn' is not installed, so not removed
Package 'libreoffice-grammarcheck-mr' is not installed, so not removed
Package 'libreoffice-help-mr' is not installed, so not removed
Package 'libreoffice-grammarcheck-nb' is not installed, so not removed
Package 'libreoffice-help-nb' is not installed, so not removed
Package 'libreoffice-grammarcheck-ne' is not installed, so not removed
Package 'libreoffice-help-ne' is not installed, so not removed
Package 'libreoffice-grammarcheck-nl' is not installed, so not removed
Package 'libreoffice-grammarcheck-nn' is not installed, so not removed
Package 'libreoffice-help-nn' is not installed, so not removed
Package 'libreoffice-grammarcheck-nr' is not installed, so not removed
Package 'libreoffice-help-nr' is not installed, so not removed
Package 'libreoffice-grammarcheck-nso' is not installed, so not removed
Package 'libreoffice-help-nso' is not installed, so not removed
Package 'libreoffice-grammarcheck-oc' is not installed, so not removed
Package 'libreoffice-help-oc' is not installed, so not removed
Package 'libreoffice-grammarcheck-om' is not installed, so not removed
Package 'libreoffice-grammarcheck-or' is not installed, so not removed
Package 'libreoffice-help-or' is not installed, so not removed
Package 'libreoffice-grammarcheck-pa-in' is not installed, so not removed
Package 'libreoffice-help-pa-in' is not installed, so not removed
Package 'libreoffice-grammarcheck-pl' is not installed, so not removed
Package 'libreoffice-grammarcheck-pt' is not installed, so not removed
Package 'libreoffice-grammarcheck-pt-br' is not installed, so not removed
Package 'libreoffice-grammarcheck-ro' is not installed, so not removed
Package 'libreoffice-help-ro' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-ru-ru' instead of 'libreoffice-grammarcheck-ru'
Package 'libreoffice-grammarcheck-rw' is not installed, so not removed
Package 'libreoffice-help-rw' is not installed, so not removed
Package 'libreoffice-grammarcheck-si' is not installed, so not removed
Package 'libreoffice-help-si' is not installed, so not removed
Package 'libreoffice-grammarcheck-sk' is not installed, so not removed
Package 'libreoffice-grammarcheck-sl' is not installed, so not removed
Package 'libreoffice-grammarcheck-sr' is not installed, so not removed
Package 'libreoffice-help-sr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ss' is not installed, so not removed
Package 'libreoffice-help-ss' is not installed, so not removed
Package 'libreoffice-grammarcheck-st' is not installed, so not removed
Package 'libreoffice-help-st' is not installed, so not removed
Package 'libreoffice-grammarcheck-sv' is not installed, so not removed
Package 'libreoffice-grammarcheck-ta' is not installed, so not removed
Package 'libreoffice-help-ta' is not installed, so not removed
Package 'libreoffice-grammarcheck-te' is not installed, so not removed
Package 'libreoffice-help-te' is not installed, so not removed
Package 'libreoffice-grammarcheck-tg' is not installed, so not removed
Package 'libreoffice-help-tg' is not installed, so not removed
Package 'libreoffice-grammarcheck-th' is not installed, so not removed
Package 'libreoffice-help-th' is not installed, so not removed
Package 'libreoffice-grammarcheck-tn' is not installed, so not removed
Package 'libreoffice-help-tn' is not installed, so not removed
Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-spellcheck-tr'
Package 'libreoffice-grammarcheck-tr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ts' is not installed, so not removed
Package 'libreoffice-help-ts' is not installed, so not removed
Package 'libreoffice-grammarcheck-ug' is not installed, so not removed
Package 'libreoffice-help-ug' is not installed, so not removed
Package 'libreoffice-grammarcheck-uk' is not installed, so not removed
Package 'libreoffice-help-uk' is not installed, so not removed
Package 'libreoffice-grammarcheck-uz' is not installed, so not removed
Package 'libreoffice-help-uz' is not installed, so not removed
Package 'libreoffice-grammarcheck-ve' is not installed, so not removed
Package 'libreoffice-help-ve' is not installed, so not removed
Package 'libreoffice-grammarcheck-vi' is not installed, so not removed
Package 'libreoffice-grammarcheck-xh' is not installed, so not removed
Package 'libreoffice-help-xh' is not installed, so not removed
Package 'libreoffice-grammarcheck-zh-cn' is not installed, so not removed
Package 'libreoffice-grammarcheck-zh-tw' is not installed, so not removed
Package 'libreoffice-grammarcheck-zu' is not installed, so not removed
Package 'libreoffice-help-zu' is not installed, so not removed
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'unity-scope-home' instead of 'unity-scope-asklibreoffice'
Package 'libreoffice.org-calc' is not installed, so not removed
Package 'libreoffice.org-writer' is not installed, so not removed
Note, selecting 'libreoffice-lightproof-en' instead of 'libreoffice-grammarcheck-en-us'
Note, selecting 'libreoffice-report-builder' instead of 'libreoffice-reportdesigner'
Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-hyphenation-tr'
Package 'libreoffice-nlpsolver' is not installed, so not removed
Package 'libreoffice-voikko' is not installed, so not removed
Package 'libreoffice-dmaths' is not installed, so not removed
Package 'libreoffice-lightproof-en' is not installed, so not removed
Package 'libreoffice-lightproof-hu' is not installed, so not removed
Package 'libreoffice-lightproof-ru-ru' is not installed, so not removed
Package 'libreoffice-templates' is not installed, so not removed
Package 'libreoffice-writer2latex' is not installed, so not removed
Package 'libreoffice-writer2xhtml' is not installed, so not removed
Package 'libreoffice-zemberek' is not installed, so not removed
Package 'openclipart-libreoffice' is not installed, so not removed
Package 'openclipart2-libreoffice' is not installed, so not removed
Package 'browser-plugin-libreoffice' is not installed, so not removed
Package 'libreoffice-emailmerge' is not installed, so not removed
Package 'libreoffice-gtk3' is not installed, so not removed
Package 'libreoffice-kde' is not installed, so not removed
Package 'libreoffice-librelogo' is not installed, so not removed
Package 'libreoffice-mysql-connector' is not installed, so not removed
Package 'libreoffice-presenter-console' is not installed, so not removed
Package 'libreoffice-report-builder' is not installed, so not removed
Package 'libreoffice-script-provider-bsh' is not installed, so not removed
Package 'libreoffice-script-provider-js' is not installed, so not removed
Package 'libreoffice-script-provider-python' is not installed, so not removed
Package 'libreoffice-sdbc-postgresql' is not installed, so not removed
Package 'libreoffice-style-crystal' is not installed, so not removed
Package 'libreoffice-style-hicontrast' is not installed, so not removed
Package 'libreoffice-style-oxygen' is not installed, so not removed
Package 'libreoffice-subsequentcheckbase' is not installed, so not removed
Package 'libreoffice-wiki-publisher' is not installed, so not removed
Package 'libreoffice-common' is not installed, so not removed
Package 'libreoffice-dbg' is not installed, so not removed
Package 'libreoffice-dev' is not installed, so not removed
Package 'libreoffice-dev-doc' is not installed, so not removed
Package 'libreoffice-help-ca' is not installed, so not removed
Package 'libreoffice-help-cs' is not installed, so not removed
Package 'libreoffice-help-da' is not installed, so not removed
Package 'libreoffice-help-de' is not installed, so not removed
Package 'libreoffice-help-dz' is not installed, so not removed
Package 'libreoffice-help-el' is not installed, so not removed
Package 'libreoffice-help-en-gb' is not installed, so not removed
Package 'libreoffice-help-en-us' is not installed, so not removed
Package 'libreoffice-help-es' is not installed, so not removed
Package 'libreoffice-help-et' is not installed, so not removed
Package 'libreoffice-help-eu' is not installed, so not removed
Package 'libreoffice-help-fi' is not installed, so not removed
Package 'libreoffice-help-fr' is not installed, so not removed
Package 'libreoffice-help-gl' is not installed, so not removed
Package 'libreoffice-help-hi' is not installed, so not removed
Package 'libreoffice-help-hu' is not installed, so not removed
Package 'libreoffice-help-it' is not installed, so not removed
Package 'libreoffice-help-ja' is not installed, so not removed
Package 'libreoffice-help-km' is not installed, so not removed
Package 'libreoffice-help-ko' is not installed, so not removed
Package 'libreoffice-help-nl' is not installed, so not removed
Package 'libreoffice-help-om' is not installed, so not removed
Package 'libreoffice-help-pl' is not installed, so not removed
Package 'libreoffice-help-pt' is not installed, so not removed
Package 'libreoffice-help-pt-br' is not installed, so not removed
Package 'libreoffice-help-ru' is not installed, so not removed
Package 'libreoffice-help-sk' is not installed, so not removed
Package 'libreoffice-help-sl' is not installed, so not removed
Package 'libreoffice-help-sv' is not installed, so not removed
Package 'libreoffice-help-tr' is not installed, so not removed
Package 'libreoffice-help-vi' is not installed, so not removed
Package 'libreoffice-help-zh-cn' is not installed, so not removed
Package 'libreoffice-help-zh-tw' is not installed, so not removed
Package 'libreoffice-l10n-af' is not installed, so not removed
Package 'libreoffice-l10n-ar' is not installed, so not removed
Package 'libreoffice-l10n-as' is not installed, so not removed
Package 'libreoffice-l10n-ast' is not installed, so not removed
Package 'libreoffice-l10n-be' is not installed, so not removed
Package 'libreoffice-l10n-bg' is not installed, so not removed
Package 'libreoffice-l10n-bn' is not installed, so not removed
Package 'libreoffice-l10n-br' is not installed, so not removed
Package 'libreoffice-l10n-bs' is not installed, so not removed
Package 'libreoffice-l10n-ca' is not installed, so not removed
Package 'libreoffice-l10n-cs' is not installed, so not removed
Package 'libreoffice-l10n-cy' is not installed, so not removed
Package 'libreoffice-l10n-da' is not installed, so not removed
Package 'libreoffice-l10n-de' is not installed, so not removed
Package 'libreoffice-l10n-dz' is not installed, so not removed
Package 'libreoffice-l10n-el' is not installed, so not removed
Package 'libreoffice-l10n-en-gb' is not installed, so not removed
Package 'libreoffice-l10n-en-za' is not installed, so not removed
Package 'libreoffice-l10n-eo' is not installed, so not removed
Package 'libreoffice-l10n-es' is not installed, so not removed
Package 'libreoffice-l10n-et' is not installed, so not removed
Package 'libreoffice-l10n-eu' is not installed, so not removed
Package 'libreoffice-l10n-fa' is not installed, so not removed
Package 'libreoffice-l10n-fi' is not installed, so not removed
Package 'libreoffice-l10n-fr' is not installed, so not removed
Package 'libreoffice-l10n-ga' is not installed, so not removed
Package 'libreoffice-l10n-gl' is not installed, so not removed
Package 'libreoffice-l10n-gu' is not installed, so not removed
Package 'libreoffice-l10n-he' is not installed, so not removed
Package 'libreoffice-l10n-hi' is not installed, so not removed
Package 'libreoffice-l10n-hr' is not installed, so not removed
Package 'libreoffice-l10n-hu' is not installed, so not removed
Package 'libreoffice-l10n-id' is not installed, so not removed
Package 'libreoffice-l10n-in' is not installed, so not removed
Package 'libreoffice-l10n-is' is not installed, so not removed
Package 'libreoffice-l10n-it' is not installed, so not removed
Package 'libreoffice-l10n-ja' is not installed, so not removed
Package 'libreoffice-l10n-ka' is not installed, so not removed
Package 'libreoffice-l10n-kk' is not installed, so not removed
Package 'libreoffice-l10n-km' is not installed, so not removed
Package 'libreoffice-l10n-ko' is not installed, so not removed
Package 'libreoffice-l10n-ku' is not installed, so not removed
Package 'libreoffice-l10n-lt' is not installed, so not removed
Package 'libreoffice-l10n-lv' is not installed, so not removed
Package 'libreoffice-l10n-mk' is not installed, so not removed
Package 'libreoffice-l10n-ml' is not installed, so not removed
Package 'libreoffice-l10n-mn' is not installed, so not removed
Package 'libreoffice-l10n-mr' is not installed, so not removed
Package 'libreoffice-l10n-nb' is not installed, so not removed
Package 'libreoffice-l10n-ne' is not installed, so not removed
Package 'libreoffice-l10n-nl' is not installed, so not removed
Package 'libreoffice-l10n-nn' is not installed, so not removed
Package 'libreoffice-l10n-nr' is not installed, so not removed
Package 'libreoffice-l10n-nso' is not installed, so not removed
Package 'libreoffice-l10n-oc' is not installed, so not removed
Package 'libreoffice-l10n-om' is not installed, so not removed
Package 'libreoffice-l10n-or' is not installed, so not removed
Package 'libreoffice-l10n-pa-in' is not installed, so not removed
Package 'libreoffice-l10n-pl' is not installed, so not removed
Package 'libreoffice-l10n-pt' is not installed, so not removed
Package 'libreoffice-l10n-pt-br' is not installed, so not removed
Package 'libreoffice-l10n-ro' is not installed, so not removed
Package 'libreoffice-l10n-ru' is not installed, so not removed
Package 'libreoffice-l10n-rw' is not installed, so not removed
Package 'libreoffice-l10n-si' is not installed, so not removed
Package 'libreoffice-l10n-sk' is not installed, so not removed
Package 'libreoffice-l10n-sl' is not installed, so not removed
Package 'libreoffice-l10n-sr' is not installed, so not removed
Package 'libreoffice-l10n-ss' is not installed, so not removed
Package 'libreoffice-l10n-st' is not installed, so not removed
Package 'libreoffice-l10n-sv' is not installed, so not removed
Package 'libreoffice-l10n-ta' is not installed, so not removed
Package 'libreoffice-l10n-te' is not installed, so not removed
Package 'libreoffice-l10n-tg' is not installed, so not removed
Package 'libreoffice-l10n-th' is not installed, so not removed
Package 'libreoffice-l10n-tn' is not installed, so not removed
Package 'libreoffice-l10n-tr' is not installed, so not removed
Package 'libreoffice-l10n-ts' is not installed, so not removed
Package 'libreoffice-l10n-ug' is not installed, so not removed
Package 'libreoffice-l10n-uk' is not installed, so not removed
Package 'libreoffice-l10n-uz' is not installed, so not removed
Package 'libreoffice-l10n-ve' is not installed, so not removed
Package 'libreoffice-l10n-vi' is not installed, so not removed
Package 'libreoffice-l10n-xh' is not installed, so not removed
Package 'libreoffice-l10n-za' is not installed, so not removed
Package 'libreoffice-l10n-zh-cn' is not installed, so not removed
Package 'libreoffice-l10n-zh-tw' is not installed, so not removed
Package 'libreoffice-l10n-zu' is not installed, so not removed
Package 'libreoffice-officebean' is not installed, so not removed
Package 'libreoffice-ogltrans' is not installed, so not removed
Package 'libreoffice-presentation-minimizer' is not installed, so not removed
Package 'libreoffice-style-tango' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python3-uno : Depends: libreoffice-core (= 1:4.1.3-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I then decided to do as suggested and got this. 
```
rufuslucky@rufuslucky-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic
  linux-image-3.11.0-12-generic linux-image-3.8.0-32-generic
  linux-image-extra-3.11.0-12-generic linux-image-extra-3.8.0-32-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/27.0 MB of archives.
After this operation, 77.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
                                                              rmdir: failed to remove ‘/var/lib/libreoffice/share/prereg/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/share/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/program/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'rufuslucky@rufuslucky-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.11.0-12 linux-headers-3.11.0-12-generic
  linux-image-3.11.0-12-generic linux-image-3.8.0-32-generic
  linux-image-extra-3.11.0-12-generic linux-image-extra-3.8.0-32-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-crystal libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-tango
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
15 not fully installed or removed.
Need to get 0 B/27.0 MB of archives.
After this operation, 77.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 316610 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714
No apport report written because MaxReports is reached already
                                                              rmdir: failed to remove ‘/var/lib/libreoffice/share/prereg/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/share/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice/program/’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
rmdir: failed to remove ‘/var/lib/libreoffice’: No such file or directory
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rufuslucky@rufuslucky-desktop:~$ 
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
rufuslucky@rufuslucky-desktop:~$ 
```

Obviously I know just enough to be dangerous, but not enough to clean up after myself. Can somebody help solve these dependency issues. Somebody who can explain things as if talking to a complete idiot. Thanks.

---

### Post by dragonfly41 on 2014-03-20
This thread has similar symptoms to yours ...

[http://askubuntu.com/questions/258738/problem-with-update-of-libreoffice](http://askubuntu.com/questions/258738/problem-with-update-of-libreoffice)

see the solution

---

### Post by exl0 on 2014-03-20
Hi dragonfly41,

SO I followed the link and did what it says and deleted folder /var/cashe/apt. Next I also turned off the ppa followed this link [http://askubuntu.com/questions/143203/how-to-disable-a-particular-ppa](http://askubuntu.com/questions/143203/how-to-disable-a-particular-ppa) .

Now I go to Ubuntu software center and a window pops up informing me that "New software cannot be installed, because there is a problem with the current software installed. Do want to repair the problem now?"

I click yes and after a while another window pops up with these errors in the detail:

 ```
i[COLOR=#222222][FONT=Verdana]nstallArchives() failed: (Reading database ... 
[/FONT][/COLOR][FONT=Verdana](Reading database ... 5%[/FONT]
[FONT=Verdana](Reading database ... 10%[/FONT]
[FONT=Verdana](Reading database ... 15%[/FONT]
[FONT=Verdana](Reading database ... 20%[/FONT]
[FONT=Verdana](Reading database ... 25%[/FONT]
[FONT=Verdana](Reading database ... 30%[/FONT]
[FONT=Verdana](Reading database ... 35%[/FONT]
[FONT=Verdana](Reading database ... 40%[/FONT]
[FONT=Verdana](Reading database ... 45%[/FONT]
[FONT=Verdana](Reading database ... 50%[/FONT]
[FONT=Verdana](Reading database ... 55%[/FONT]
[FONT=Verdana](Reading database ... 60%[/FONT]
[FONT=Verdana](Reading database ... 65%[/FONT]
[FONT=Verdana](Reading database ... 70%[/FONT]
[FONT=Verdana](Reading database ... 75%[/FONT]
[FONT=Verdana](Reading database ... 80%[/FONT]
[FONT=Verdana](Reading database ... 85%[/FONT]
[FONT=Verdana](Reading database ... 90%[/FONT]
[FONT=Verdana](Reading database ... 95%[/FONT]
[FONT=Verdana](Reading database ... 100%[/FONT]
[FONT=Verdana](Reading database ... 211883 files and directories currently installed.)[/FONT]
[FONT=Verdana]Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...[/FONT]
[FONT=Verdana]dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):[/FONT]
[FONT=Verdana] trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714[/FONT]
[FONT=Verdana]No apport report written because MaxReports is reached already[/FONT]
[FONT=Verdana]rmdir: failed to remove /var/lib/libreoffice/share/prereg/: No such file or directory[/FONT]
[FONT=Verdana]rmdir: failed to remove /var/lib/libreoffice/share/: No such file or directory[/FONT]
[FONT=Verdana]rmdir: failed to remove /var/lib/libreoffice/program/: No such file or directory[/FONT]
[FONT=Verdana]rmdir: failed to remove /var/lib/libreoffice: No such file or directory[/FONT]
[FONT=Verdana]rmdir: failed to remove /var/lib/libreoffice: No such file or directory[/FONT]
[FONT=Verdana]Processing triggers for man-db ...[/FONT]
[FONT=Verdana]Processing triggers for gnome-icon-theme ...[/FONT]
[FONT=Verdana]Processing triggers for hicolor-icon-theme ...[/FONT]
[FONT=Verdana]Processing triggers for shared-mime-info ...[/FONT]
[FONT=Verdana]Processing triggers for desktop-file-utils ...[/FONT]
[FONT=Verdana]Processing triggers for gnome-menus ...[/FONT]
[FONT=Verdana]Processing triggers for bamfdaemon ...[/FONT]
[FONT=Verdana]Rebuilding /usr/share/applications/bamf-2.index...[/FONT]
[FONT=Verdana]Processing triggers for mime-support ...[/FONT]
[FONT=Verdana]Errors were encountered while processing:[/FONT]
[FONT=Verdana] /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb[/FONT]
[FONT=Verdana]Error in function: [/FONT]
[FONT=Verdana]dpkg: dependency problems prevent configuration of libreoffice-java-common:[/FONT]
[FONT=Verdana] libreoffice-java-common depends on libreoffice-common; however:[/FONT]
[FONT=Verdana]  Package libreoffice-common is not installed.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]dpkg: error processing libreoffice-java-common (--configure):[/FONT]
[FONT=Verdana] dependency problems - leaving unconfigured[/FONT]
[FONT=Verdana]dpkg: dependency problems prevent configuration of libreoffice-base:[/FONT]
[FONT=Verdana] libreoffice-base depends on libreoffice-java-common (>= 1:4.1.3~); however:[/FONT]
[FONT=Verdana]  Package libreoffice-java-common is not configured yet.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]dpkg: error processing libreoffice-base (--configure):[/FONT]
[FONT=Verdana] dependency problems - leaving unconfigured[/FONT]
[FONT=Verdana]dpkg: dependency problems prevent configuration of libreoffice-report-builder-bin:[/FONT]
[FONT=Verdana] libreoffice-report-builder-bin depends on libreoffice-base; however:[/FONT]
[FONT=Verdana]  Package libreoffice-base is not configured yet.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]dpkg: error processing libreoffice-report-builder-bin (--configure):[/FONT]
[FONT=Verdana] dependency problems - leaving unconfigured[/FONT]
[FONT=Verdana]dpkg: dependency problems prevent configuration of libreoffice-core:[/FONT]
[FONT=Verdana] libreoffice-core depends on libreoffice-common (>> 1:4.1.3); however:[/FONT]
[FONT=Verdana]  Package libreoffice-common is not installed.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]dpkg: error processing libreoffice-core (--configure):[/FONT]
[FONT=Verdana] dependency problems - leaving unconfigured[/FONT]
[FONT=Verdana]dpkg: dependency problems prevent configuration of python3-uno:[/FONT]
[FONT=Verdana] python3-uno depends on libreoffice-core (= 1:4.1.3-0ubuntu1); however:[/FONT]
[FONT=Verdana]  Package libreoffice-core is not configured yet.[/FONT]
[FONT=Verdana]
[/FONT]
[FONT=Verdana]dpkg: error processing python3-uno (--configure):[/FONT]
[FONT=Verdana] dependency problems - leaving unconfigured[/FONT]
[FONT=Verdana]dpkg: dependency problems prevent configuration of libreoffice-math:[/FONT]
[FONT=Verdana] libreoffice-math depends on libreoffice-core (= 1:4.1.3-0ubuntu1); however:[/FONT]
This is the same message I was getting prior to follow the instruction in your link.
``` 

Any other possible solutions?

Thanks!


> **dragonfly41 said:**
> This thread has similar symptoms to yours ...

[http://askubuntu.com/questions/258738/problem-with-update-of-libreoffice](http://askubuntu.com/questions/258738/problem-with-update-of-libreoffice)

see the solution

---

### Post by dragonfly41 on 2014-03-20
I can only suggest that you try using  ..

Applications > System Tools > Administration > Synaptic Package Manager   (not Ubuntu Software Centre)

to search for old packages and dependencies to be removed and then fresh installation.

---

### Post by exl0 on 2014-03-21
Hi dragonfly41,

Thanks for your reply. Unfortunately, I don't have Synaptic Package Manager installed in my system.


> **dragonfly41 said:**
> I can only suggest that you try using  ..

Applications > System Tools > Administration > Synaptic Package Manager   (not Ubuntu Software Centre)

to search for old packages and dependencies to be removed and then fresh installation.

---

### Post by deadflowr on 2014-03-21
> **exl0 said:**
> Hi dragonfly41,

Thanks for your reply. Unfortunately, I don't have Synaptic Package Manager installed in my system.


Off hand, do you have open office installed?

Meaning, did you install open office?

---

### Post by dragonfly41 on 2014-03-22
> Unfortunately, I don't have Synaptic Package Manager installed in my system.

You can install Synaptic Package Manager from Ubuntu Software Centre .. search "Synaptic".

---

### Post by ian-weisser on 2014-03-22
When dpkg fails to install a package, it tells you *exactly* why it failed.
dpkg has been telling you what it thinks the problem is in each error message.

> **exl0 said:**
> 
 ```
[FONT=Verdana]...
Unpacking libreoffice-common (from .../libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb) ...[/FONT]
[FONT=Verdana]dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a4.1.3-0ubuntu1_all.deb (--unpack):[/FONT]
[COLOR=#ff0000]**[FONT=Verdana] trying to overwrite '/usr/bin/soffice', which is also in package openoffice-debian-menus 4.0-9714[/FONT]**[/COLOR]
...

``` 


Your system thinks that you have a package installed, [FONT=Verdana]openoffice-debian-menus, [/FONT]which conflicts with libreoffice-common.
They both provide at least one of the same files (/usr/bin/soffice), and that's a conflict in dpkg.

Do you have openoffice-debian-menus installed?
Does the file /usr/bin/soffice exist (working or not) on your system?
If so, uninstall the openoffice-debian-menus package. Do NOT manually rm any files. That won't help

After you have removed openoffice-debian-menus, then libreoffice-common should be able to install.

---

### Post by exl0 on 2014-03-22
Hi guys, thanks to you all for replying.

The problem here is that I can't install or remove any software either using the apt-get or the software center. The error code I posted was always the response. It seems that the system is trying to finish with the libreoffice installation no matter what else happens, and it just can't finish the installation process because of the broken dependencies.

Yes the whole mess started when I was trying to install/remove between openoffice and libreoffice.

I did follow one thread I found on the internet and manually removed /usr/bin/soffice. The subsequent procedure didn't work for me. The funny thing is, I can still run openoffice from the icon pinned on the sidebar.

I think my problem is exactly like Dragonfly's, except I can't install the Synaptic Package Manager to repair the broken dependencies.

I even tried to compile the Synaptic source code, but gave up for the missing libraries needed to finish the compilation. Again, can't install those libraries.


> **ian-weisser said:**
> When dpkg fails to install a package, it tells you *exactly* why it failed.
dpkg has been telling you what it thinks the problem is in each error message.



Your system thinks that you have a package installed, [FONT=Verdana]openoffice-debian-menus, [/FONT]which conflicts with libreoffice-common.
They both provide at least one of the same files (/usr/bin/soffice), and that's a conflict in dpkg.

Do you have openoffice-debian-menus installed?
Does the file /usr/bin/soffice exist (working or not) on your system?
If so, uninstall the openoffice-debian-menus package. Do NOT manually rm any files. That won't help

After you have removed openoffice-debian-menus, then libreoffice-common should be able to install.

---

### Post by deadflowr on 2014-03-22
So when you installed open(I'll go by shorten terms for ease of writing) did you first remove/purge libre?
And then after removing libre, installed open.
And then tried to install libre again?

My somewhat understanding of it is that while it is possible to install both, you have to install them manually, rather then through the repo system.
Perhaps a purge of libre, maybe.

Can you
```
sudo apt-get purge libreoffice*
```
or 
```
sudo apt-get purge openoffice*
```

---

### Post by exl0 on 2014-03-22
Hi Ian,

It turns out you are absolutely right. After I did a "sudo dpkg -r openoffice-debian-menus", I am able to finish the "sudo apt-get -f install" that previously stalled. Now everything is fine, and I even have both libreoffice and openoffice on my system.

I also just installed the Synaptic Package Manager too.

Thank you Ian sooooo much!

:-)

> **ian-weisser said:**
> When dpkg fails to install a package, it tells you *exactly* why it failed.
dpkg has been telling you what it thinks the problem is in each error message.



Your system thinks that you have a package installed, [FONT=Verdana]openoffice-debian-menus, [/FONT]which conflicts with libreoffice-common.
They both provide at least one of the same files (/usr/bin/soffice), and that's a conflict in dpkg.

Do you have openoffice-debian-menus installed?
Does the file /usr/bin/soffice exist (working or not) on your system?
If so, uninstall the openoffice-debian-menus package. Do NOT manually rm any files. That won't help

After you have removed openoffice-debian-menus, then libreoffice-common should be able to install.

---

### Post by ian-weisser on 2014-03-22
> **exl0 said:**
> The problem here is that I can't install or remove any software either using the apt-get or the software center.

Oh, when apt-get and other frontends to dpkg fail, then use dpkg directly.
*Use dpkg sparingly and thoughtfully. It lacks safeguards to keep you from breaking your system(...more).*

```
sudo dpkg --remove openoffice-debian-menus
sudo apt-get install libreoffice
```

The first line removes the problem openoffice-debian-menus package without using apt-get or Synaptic or Software Center.
After the offending package is removed, apt-get, Synaptic, and Software Center should work. 

If it works, your problem is fixed.
If it doesn't work, read the error message carefully.
If you don't understand the error, post it here.

---

### Post by exl0 on 2014-03-22
Hi Ian,

Thanks again. I almost gave up and thought about reinstalling my system all over again. I certainly did not know how to read that error message.

An off topic question, do you have a suggestion as to what utility to use to back up my computer? I am reading a little bit from this link [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem). I have a 3TB hard disk installed on my home network. Ideally if I could back up not just my home directory but the whole system once a week, that will be great.

Ed

> **ian-weisser said:**
> Oh, when apt-get and other frontends to dpkg fail, then use dpkg directly.
*Use dpkg sparingly and thoughtfully. It lacks safeguards to keep you from breaking your system.*

```
sudo dpkg --remove openoffice-debian-menus
sudo apt-get install libreoffice
```

The first line removes the problem openoffice-debian-menus package without using apt-get or Synaptic or Software Center.
After the offending package is removed, apt-get, Synaptic, and Software Center should work. 

If it works, your problem is fixed.
If it doesn't work, read the error message carefully.
If you don't understand the error, post it here.

---

### Post by ian-weisser on 2014-03-22
> **exl0 said:**
> An off topic question, do you have a suggestion as to what utility to use to back up my computer? .... Ideally if I could back up not just my home directory but the whole system once a week, that will be great.

There are lots of choices. The default Ubuntu application is Deja Dup, and it has a large community of users here - I would suggest trying it first. It's schedulable, works well over a network, easy to restore from, build on top of the stable 'duplicicty' command-line application, and is easy to use. It lacks some advanced settings for atypical use, but your usage seems typical to me.

Generally, you can back up your entire system...but you don't need to. Back up your /home data, which includes your mail and browser profiles and keyring and other personal stuff. I suppose you can back up parts of /etc to preserve network settings and parts of /var to preserve your list of installed packages...but I don't. My network settings are written in the kitchen for guests to use anyway. Software Center makes re-finding applications tremendously easy...it's harder to remember to prune away the applications you no longer use. And I have only had to restore data from backups once in 10 years (my own fault, not a system failure).

---

