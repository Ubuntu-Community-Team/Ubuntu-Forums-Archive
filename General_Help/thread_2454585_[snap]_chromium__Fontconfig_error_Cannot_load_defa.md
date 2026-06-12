---
title: "[snap] chromium : Fontconfig error: Cannot load default config file"
date: 2020-12-02
forum: General Help
---

### Post by dino99 on 2020-12-02
Journal expose some suspicious errors;

 [PHP]apparmor="DENIED" operation="open" profile="snap.chromium.chromium" name="/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/busnum" pid=2486 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
 apparmor="DENIED" operation="open" profile="snap.chromium.chromium" name="/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/devnum" pid=2486 comm="ThreadPoolForeg" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
 chromium_chromium.desktop[2930]: Fontconfig error: Cannot load default config file

chromium_chromium.desktop[2643]: [2643:2647:1202/082104.495232:ERROR:ssl_client_socket_impl.cc(960)] handshake failed; returned -1, SSL error code 1, net_error -107[/PHP]

How can i resolve that fontconfig load ?  Is it related to apparmor 'DENIED' What to do ?

That cause , after a while, a high cpu usage and finally a general system freeze.

---

