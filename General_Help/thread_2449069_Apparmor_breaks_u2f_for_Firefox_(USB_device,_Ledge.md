---
title: "Apparmor breaks u2f for Firefox (USB device, Ledger Nano S)"
date: 2020-08-19
forum: General Help
---

### Post by fluffy20470-50233 on 2020-08-19
I have a USB device (Ledger Nano S) that I'm able to use with the native desktop application. However, I was unable to use it with Firefox (websites like myetherwallet & mycrypto gave me "u2f error" messages). I solved this by using the following commands. 
```
sudo systemctl stop apparmor
sudo systemctl disable apparmor
```

This allows me to use my Ledger Nano S with Firefox (websites like mytherwallet & mycrypto work properly). However, I would prefer to not completely disable apparmor. 

These are my profiles before disabling apparmor:
```
50 profiles are loaded.
40 profiles are in enforce mode.
   /snap/core/9804/usr/lib/snapd/snap-confine
   /snap/core/9804/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/bin/man
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/tcpdump
   /{,usr/}sbin/dhclient
   firefox//browser_java
   firefox//browser_openjdk
   firefox//sanitized_helper
   ippusbxd
   libreoffice-senddoc
   libreoffice-soffice//gpg
   libreoffice-xpdfimport
   libvirtd
   libvirtd//qemu_bridge_helper
   lsb_release
   man_filter
   man_groff
   nvidia_modprobe
   nvidia_modprobe//kmod
   snap-update-ns.chromium
   snap-update-ns.core
   snap-update-ns.pulsemixer
   snap-update-ns.software-boutique
   snap-update-ns.ubuntu-mate-welcome
   snap.chromium.chromedriver
   snap.chromium.chromium
   snap.core.hook.configure
   snap.pulsemixer.pulsemixer
   virt-aa-helper
10 profiles are in complain mode.
   firefox
   firefox//lsb_release
   libreoffice-oopslash
   libreoffice-soffice
   snap.software-boutique.software-boutique
   snap.ubuntu-mate-welcome.hook.install
   snap.ubuntu-mate-welcome.hook.post-refresh
   snap.ubuntu-mate-welcome.hook.remove
   snap.ubuntu-mate-welcome.software-boutique
   snap.ubuntu-mate-welcome.ubuntu-mate-welcome
```

These are my profiles after disabling apparmor (using: sudo systemctl stop apparmor > sudo systemctl disable apparmor)
```
17 profiles are loaded.
11 profiles are in enforce mode.
   /snap/core/9804/usr/lib/snapd/snap-confine
   /snap/core/9804/usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   snap-update-ns.chromium
   snap-update-ns.core
   snap-update-ns.pulsemixer
   snap-update-ns.software-boutique
   snap-update-ns.ubuntu-mate-welcome
   snap.chromium.chromedriver
   snap.chromium.chromium
   snap.core.hook.configure
   snap.pulsemixer.pulsemixer
6 profiles are in complain mode.
   snap.software-boutique.software-boutique
   snap.ubuntu-mate-welcome.hook.install
   snap.ubuntu-mate-welcome.hook.post-refresh
   snap.ubuntu-mate-welcome.hook.remove
   snap.ubuntu-mate-welcome.software-boutique
   snap.ubuntu-mate-welcome.ubuntu-mate-welcome
```


I would prefer to not use:
```
sudo systemctl stop apparmor > sudo systemctl disable apparmor
```

How can I fix u2f for Firefox without completely disabling apparmor?

---

### Post by deadflowr on 2020-08-19
Not sure what's going on with your firefox, but Ubuntu's firefox ships with the apparmor profile disabled.
You can reset it to disabled if you somehow enabled it by
running
```
sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.firefox
```
apparmor reference here: [https://help.ubuntu.com/community/AppArmor#Disable_one_profile]("https://help.ubuntu.com/community/AppArmor#Disable_one_profile")

---

### Post by fluffy20470-50233 on 2020-08-20
> **deadflowr said:**
> Not sure what's going on with your firefox, but Ubuntu's firefox ships with the apparmor profile disabled.
You can reset it to disabled if you somehow enabled it by
running
```
sudo ln -s /etc/apparmor.d/usr.bin.firefox /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.bin.firefox
```
apparmor reference here: [https://help.ubuntu.com/community/AppArmor#Disable_one_profile](https://help.ubuntu.com/community/AppArmor#Disable_one_profile)

Thank you. problem solved!

---

