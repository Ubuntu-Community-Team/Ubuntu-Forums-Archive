---
title: "Updating without synaptic"
date: 2005-03-27
forum: General Help
---

### Post by theChauvinist on 2005-03-27
I wish to upgrade my Thunderbird installation to the latest 1.0.2 release, but this release doesn't seem to be available throught the Synaptic Package Manager yet.

Could someone please let me know how to upgrade Thunderbird? I'm guessing if I just install from mozilla.org then I'll have two installs...

---

### Post by istoyanov on 2005-03-27
1) Go and get the *.tar.gz from mozilla.org

2) unpack it to /opt

3) rename the original /usr/bin/thunderbird to /usr/bin/thunderbird.old

3) place a symlink to /opt/thunderbird/thunderbird in /usr/bin.

If you remove the old version of Thunderbird, step 3) will be unnecessary.

HTH!

---

### Post by ubuntu_demon on 2005-03-27
[QUOTE=theChauvinist]I wish to upgrade my Thunderbird installation to the latest 1.0.2 release, but this release doesn't seem to be available throught the Synaptic Package Manager yet.

Could someone please let me know how to upgrade Thunderbird? I'm guessing if I just install from mozilla.org then I'll have two installs...[/QUOTE]
 IF you don't know how to grab binaries / sources from the mozilla thunderbird website why do you want to do it then ? If you use the package from synaptic it gets updated with security fixes.

---

### Post by clb137 on 2005-03-27
Hello,

Just remember if you update yourself, you will loose the security updates from the Ubuntu  site (using apt-get os synaptic and you have to keep an eye on the updates at Mozilla site.

take care

clinton

---

