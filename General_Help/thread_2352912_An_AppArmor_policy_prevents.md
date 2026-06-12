---
title: "An AppArmor policy prevents"
date: 2017-02-16
forum: General Help
---

### Post by milesinnz on 2017-02-16
An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.82" (uid=1000 pid=2306 comm="/usr/lib/gvfs/gvfs-udisks2-volume-monitor ") interface="org.freedesktop.UDisks2.Filesystem" member="Mount" error name="(unset)" requested_reply="0" destination=":1.29" (uid=0 pid=1361 comm="/snap/udisks2/9/libexec/udisks2/udisksd ").

Can only access the system disk... all 3 other data disks return the same fault.. just came out of the blue - although I did install TeamViewer (remote desktop), since uninstalled...

apparmor module is loaded.
34 profiles are loaded.
34 profiles are in enforce mode.
   /sbin/dhclient
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-previewer//sanitized_helper
   /usr/bin/evince-thumbnailer
   /usr/bin/evince-thumbnailer//sanitized_helper
   /usr/bin/evince//sanitized_helper
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/NetworkManager/nm-dhcp-helper
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/lib/lightdm/lightdm-guest-session
   /usr/lib/lightdm/lightdm-guest-session//chromium
   /usr/lib/snapd/snap-confine
   /usr/lib/snapd/snap-confine//mount-namespace-capture-helper
   /usr/lib/telepathy/mission-control-5
   /usr/lib/telepathy/telepathy-*
   /usr/lib/telepathy/telepathy-*//pxgsettings
   /usr/lib/telepathy/telepathy-*//sanitized_helper
   /usr/lib/telepathy/telepathy-ofono
   /usr/sbin/cups-browsed
   /usr/sbin/cupsd
   /usr/sbin/cupsd//third_party
   /usr/sbin/ippusbxd
   /usr/sbin/tcpdump
   snap.core.hook.configure
   snap.slashlock.slashlock
   snap.udisks2.udisksctl
   snap.udisks2.udisksd
   snap.ultimate-media-downloader.ultimate-media-downloader
   udm-extractor
   unity8-dash
   webbrowser-app
   webbrowser-app//oxide_helper
0 profiles are in complain mode.
4 processes have profiles defined.
4 processes are in enforce mode.
   /sbin/dhclient (1301) 
   /usr/sbin/cups-browsed (1137) 
   /usr/sbin/cupsd (1098) 
   snap.udisks2.udisksd (1361) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

---

### Post by drknopfler on 2017-02-19
Hi. I have the same message since a couple of days. My ubuntu: Ubuntu 16.04.2 LTS 64-bit. 
I don't know why this happened. Ubuntu is unable to mount every usb that I conected and the only way to access to them is via dropbox-Windows7 :(
I'll keep on trying to solve this...

---

### Post by milesinnz on 2017-02-19
Hi, This applied to sata disks as well..  I tried to disable AppArmor but couldn't stop it. I was running 16.10 .... I added some remote terminal software and wondered if that had set something for some erroneous security reason. Tried some suggested fixes that were to be applied to outdated software, no good, so bit the bullet and reinstalled.. went to 16.04.2 LTS and up and running.. thought there might have been some smart people out there with a fix...

---

### Post by mc4man on 2017-02-20
Are you using unity8?
Also shows using a snap(s) of udisks2, why?

---

