---
title: "cant install python"
date: 2019-12-02
forum: General Help
---

### Post by mwieting on 2019-12-02
I am running a program called HomeAssistant and it requires python. When i try installing i get the following and im not sure how to fix it.

```

root@hassio:~# sudo apt-get install python3.6
Reading package lists... Done
Building dependency tree
Reading state information... Done
python3.6 is already the newest version (3.6.9-1~18.04).
The following packages were automatically installed and are no longer required:
  libexpat1-dev libjs-async libjs-inherits libjs-node-uuid libjs-underscore libpython-all-dev
  libpython-dev libpython2.7 libpython2.7-dev libpython3-dev libpython3.6-dev libu2f-udev
  libuv1-dev node-abbrev node-ansi node-ansi-color-table node-archy node-async node-balanced-match
  node-block-stream node-brace-expansion node-builtin-modules node-combined-stream node-concat-map
  node-cookie-jar node-delayed-stream node-forever-agent node-form-data node-fs.realpath
  node-fstream node-fstream-ignore node-github-url-from-git node-glob node-graceful-fs
  node-hosted-git-info node-inflight node-inherits node-ini node-is-builtin-module node-isexe
  node-json-stringify-safe node-lockfile node-lru-cache node-mime node-minimatch node-mkdirp
  node-mute-stream node-node-uuid node-nopt node-normalize-package-data node-npmlog node-once
  node-osenv node-path-is-absolute node-pseudomap node-qs node-read node-read-package-json
  node-request node-retry node-rimraf node-semver node-sha node-slide node-spdx-correct
  node-spdx-expression-parse node-spdx-license-ids node-tar node-tunnel-agent node-underscore
  node-validate-npm-package-license node-which node-wrappy node-yallist python3.6-dev
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 48 not upgraded.
54 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
/usr/share/python3/runtime.d/byobu.rtupdate: 5: /usr/share/python3/runtime.d/byobu.rtupdate: py3clean: not found
error running python rtupdate hook byobu
/usr/share/python3/runtime.d/dh-python.rtupdate: 5: /usr/share/python3/runtime.d/dh-python.rtupdate: py3clean: not found
error running python rtupdate hook dh-python
/usr/share/python3/runtime.d/sosreport.rtupdate: 5: /usr/share/python3/runtime.d/sosreport.rtupdate: py3clean: not found
error running python rtupdate hook sosreport
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of python3-cffi-backend:
 python3-cffi-backend depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-cffi-backend depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-cffi-backend depends on python3:any (>= 3.1~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-cffi-backend (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-async-timeout:
 python3-async-timeout depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-async-timeout (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-keyring:
 python3-keyring depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-keyring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-commandnotfound:
 python3-commandnotfound depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-commandnotfound (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-crypto:
 python3-crypto depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-crypto depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-crypto depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-crypto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-constantly:
 python3-constantly depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-constantly (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-requests-unixsocket:
 python3-requests-unixsocket depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-requests-unixsocket (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-common:
 language-selector-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package language-selector-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-click:
 python3-click depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-click (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-xdg:
 python3-xdg depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-xdg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-keyrings.alt:
 python3-keyrings.alt depends on python3-crypto; however:
  Package python3-crypto is not configured yet.
 python3-keyrings.alt depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-keyrings.alt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-colorama:
 python3-colorama depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-colorama (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-certifi:
 python3-certifi depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-certifi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-multidict:
 python3-multidict depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-multidict depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-multidict depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-multidict (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-wheel:
 python3-wheel depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-wheel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gi-cairo:
 python3-gi-cairo depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-gi-cairo depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-gi-cairo depends on python3:any (>= 3.3~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gi-cairo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-apport depends on python3-requests-unixsocket; however:
  Package python3-requests-unixsocket is not configured yet.

dpkg: error processing package python3-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apparmor:
 python3-apparmor depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apparmor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-asn1crypto:
 python3-asn1crypto depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-asn1crypto (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-blinker:
 python3-blinker depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-blinker (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-debconf:
 python3-debconf depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-debconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-oauthlib:
 python3-oauthlib depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.
 python3-oauthlib depends on python3-blinker; however:
  Package python3-blinker is not configured yet.

dpkg: error processing package python3-oauthlib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-chardet:
 python3-chardet depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-chardet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sosreport:
 sosreport depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package sosreport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-systemd:
 python3-systemd depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-systemd depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-systemd depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-systemd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-virtualenv:
 python3-virtualenv depends on python3; however:
  Package python3 is not configured yet.
 python3-virtualenv depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-virtualenv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-pip:
 python3-pip depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-pip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-requests:
 python3-requests depends on python3-certifi; however:
  Package python3-certifi is not configured yet.
 python3-requests depends on python3-chardet (<< 3.1.0); however:
  Package python3-chardet is not configured yet.
 python3-requests depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.
 python3-requests depends on python3-chardet (>= 3.0.2); however:
  Package python3-chardet is not configured yet.

dpkg: error processing package python3-requests (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-attr:
 python3-attr depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-attr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-openssl:
 python3-openssl depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-openssl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-cairo:amd64:
 python3-cairo:amd64 depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-cairo:amd64 depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-cairo:amd64 depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-cairo:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-twisted:
 python3-twisted depends on python3-constantly; however:
  Package python3-constantly is not configured yet.
 python3-twisted depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-twisted depends on python3-openssl; however:
  Package python3-openssl is not configured yet.

dpkg: error processing package python3-twisted (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-service-identity:
 python3-service-identity depends on python3-attr; however:
  Package python3-attr is not configured yet.
 python3-service-identity depends on python3-openssl; however:
  Package python3-openssl is not configured yet.
 python3-service-identity depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-service-identity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-configobj:
 python3-configobj depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-configobj (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of blueman:
 blueman depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 blueman depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 blueman depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 blueman depends on python3-cairo; however:
  Package python3-cairo:amd64 is not configured yet.
 blueman depends on python3-gi-cairo; however:
  Package python3-gi-cairo is not configured yet.

dpkg: error processing package blueman (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-setuptools:
 python3-setuptools depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-setuptools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-secretstorage:
 python3-secretstorage depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-secretstorage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-automat:
 python3-automat depends on python3-attr; however:
  Package python3-attr is not configured yet.
 python3-automat depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-automat (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dh-python:
 dh-python depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package dh-python (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-debian:
 python3-debian depends on python3-chardet; however:
  Package python3-chardet is not configured yet.
 python3-debian depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-debian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ssh-import-id:
 ssh-import-id depends on python3-requests (>= 1.1.0); however:
  Package python3-requests is not configured yet.
 ssh-import-id depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ssh-import-id (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distutils:
 python3-distutils depends on python3 (>= 3.6.7-1~); however:
  Package python3 is not configured yet.
 python3-distutils depends on python3 (<< 3.9); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-distutils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cloud-init:
 cloud-init depends on python3; however:
  Package python3 is not configured yet.
 cloud-init depends on python3-requests; however:
  Package python3-requests is not configured yet.
 cloud-init depends on python3-configobj; however:
  Package python3-configobj is not configured yet.
 cloud-init depends on python3-oauthlib; however:
  Package python3-oauthlib is not configured yet.
 cloud-init depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package cloud-init (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-common depends on python3; however:
  Package python3 is not configured yet.
 software-properties-common depends on python3-software-properties (= 0.96.24.32.11); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing package software-properties-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-cryptography:
 python3-cryptography depends on python3 (>= 3~); however:
  Package python3 is not configured yet.
 python3-cryptography depends on python3-asn1crypto (>= 0.21.0~); however:
  Package python3-asn1crypto is not configured yet.
 python3-cryptography depends on python3-cffi-backend-api-min (<= 9729); however:
  Package python3-cffi-backend-api-min is not installed.
  Package python3-cffi-backend which provides python3-cffi-backend-api-min is not configured yet.
 python3-cryptography depends on python3-cffi-backend-api-max (>= 9729); however:
  Package python3-cffi-backend-api-max is not installed.
  Package python3-cffi-backend which provides python3-cffi-backend-api-max is not configured yet.
 python3-cryptography depends on python3:any (>= 3.4~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-cryptography (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distro-info:
 python3-distro-info depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-distro-info (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ufw:
 ufw depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ufw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apt:
 python3-apt depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-apt depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.
 python3-apt depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 python3
 python3-cffi-backend
 python3-async-timeout
 python3-keyring
 python3-commandnotfound
 python3-crypto
 python3-constantly
 python3-requests-unixsocket
 language-selector-common
 python3-click
 python3-xdg
 python3-keyrings.alt
 python3-colorama
 python3-certifi
 python3-multidict
 python3-wheel
 python3-gi-cairo
 python3-apport
 python3-apparmor
 python3-asn1crypto
 python3-blinker
 python3-debconf
 python3-oauthlib
 python3-chardet
 sosreport
 python3-systemd
 python3-virtualenv
 python3-pip
 python3-requests
 python3-attr
 python3-openssl
 python3-software-properties
 python3-cairo:amd64
 python3-twisted
 python3-service-identity
 python3-configobj
 blueman
 python3-setuptools
 python3-secretstorage
 python3-automat
 dh-python
 python3-debian
 ssh-import-id
 python3-distutils
 python3-distupgrade
 cloud-init
 software-properties-common
 python3-cryptography
 python3-distro-info
 ufw
 python3-apt
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@hassio:~#
```

---

### Post by mörgæs on 2019-12-02
You have marked the thread solved and thanks for that. 
Please also post the solution for others to see.

---

### Post by mwieting on 2019-12-02
Im sorry. i must have accidentally marked the post as solved.

---

### Post by mörgæs on 2019-12-03
Ok. Why are you installing Python? Buntu contains Python 3 by default.

---

### Post by Impavidus on 2019-12-03
The install script complains that it cannot find py3clean, which should be installed as part of python3-minimal. Let's have a look at those:```
stat /usr/bin/py3clean
dpkg --list python3-minimal
```
And indeed, Python 3 is installed by default. Many core functions of Ubuntu depend on it, so you can't really remove it and still have a functioning Ubuntu system.

---

