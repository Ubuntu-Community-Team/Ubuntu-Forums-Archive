---
title: "[ubuntu] Remove &quot;Input Method&quot; and &quot;Language Support&quot;"
date: 2019-09-05
forum: General Help
---

### Post by sudoranger on 2019-09-05
Hi, I'm currently using Ubuntu 18.04 and 19.04 interchangeably. I'm only using English (United States) as my primary language and no other languages.

Now, I want to delete the "Input Method" and "Language Support" features. This includes removing the icon from the "Show Applications" menu and purging them completely from the system.

I tried removing them like this:

```
sudo apt list --installed | grep language

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


language-pack-en/bionic-updates,bionic-updates,now 1:18.04+20190718 all [installed]
language-pack-en-base/bionic-updates,bionic-updates,now 1:18.04+20180712 all [installed]
language-pack-gnome-en/bionic-updates,bionic-updates,now 1:18.04+20190718 all [installed]
language-pack-gnome-en-base/bionic-updates,bionic-updates,now 1:18.04+20180712 all [installed]
language-selector-common/bionic-updates,bionic-updates,now 0.188.3 all [installed,automatic]
language-selector-gnome/bionic-updates,bionic-updates,now 0.188.3 all [installed]

sudo apt purge language-selector* --simulate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'language-selector-common' for glob 'language-selector*'
Note, selecting 'language-selector' for glob 'language-selector*'
Note, selecting 'language-selector-gnome' for glob 'language-selector*'
Package 'language-selector' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  apg gnome-control-center-faces gnome-online-accounts libcolord-gtk1
  libgmime-3.0-0 libgrilo-0.3-0 libgtop-2.0-11 libgtop2-common
  libnss-myhostname libtotem-plparser-common libtotem-plparser18
  libwhoopsie-preferences0 mobile-broadband-provider-info
  network-manager-gnome python3-macaroonbakery python3-nacl python3-protobuf
  python3-pymacaroons python3-rfc3339 python3-tz ubuntu-system-service
  whoopsie-preferences
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  gnome-control-center* language-selector-common* language-selector-gnome*
  ubuntu-standard*
0 upgraded, 0 newly installed, 4 to remove and 2 not upgraded.
Purg gnome-control-center [1:3.28.2-0ubuntu0.18.04.4]
Purg language-selector-gnome [0.188.3]
Purg ubuntu-standard [1.417.3]



```

As you can see, this will also remove the "gnome-control-center*" and "ubuntu-standard". Now, I don't want that because it will utterly make my system useless because this will also remove the "Settings/Control Center". It seems that it is not possible to remove them as some other programs are also depending on it.

Any idea, how to safely remove only this 2 items? I don't plan to install other languages in the future just using English (US). For those wondering why I need to do this, I made a script to minimize the minimal installation of Ubuntu. I managed to remove most of the things but only encounter issue with these 2 apps. Can someone help me and thanks in advance!

---

