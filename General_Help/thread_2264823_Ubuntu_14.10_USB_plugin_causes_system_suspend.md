---
title: "Ubuntu 14.10 USB plugin causes system suspend"
date: 2015-02-10
forum: General Help
---

### Post by waqas-darkworks on 2015-02-10
Hi,

I am facing a problem whenever I plugin anything into any usb port be it a printer a flash drive or a scanner my system goes into suspend mode and then I have to press a key to wake it back up again, when I have the charger pluged in I do not face this problem so this happens only on battery, anyone has any Idea? I upgraded my bios to latest version and tried to upgrade from 14.04 to 14.10 but nothing seems to work.

this is what log looks like when I insert a USB
```

Feb 10 20:23:36 waqas-Aspire-5732Z kernel: [ 4074.408700] systemd-logind[987]: Suspend key pressed.
Feb 10 20:23:36 waqas-Aspire-5732Z kernel: [ 4074.445049] systemd-logind[987]: Suspend key pressed.
Feb 10 20:23:36 waqas-Aspire-5732Z kernel: [ 4074.480962] systemd-logind[987]: Suspend key pressed.
Feb 10 20:23:36 waqas-Aspire-5732Z kernel: [ 4074.513113] systemd-logind[987]: Suspend key pressed.
Feb 10 20:23:36 waqas-Aspire-5732Z kernel: [ 4074.544923] systemd-logind[987]: Suspend key pressed.
Feb 10 20:23:36 waqas-Aspire-5732Z kernel: [ 4074.576896] systemd-logind[987]: Suspend key pressed.
Feb 10 20:23:36 waqas-Aspire-5732Z dbus[710]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.20" (uid=0 pid=1592 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=928 comm="NetworkManager ")
Feb 10 20:23:46 waqas-Aspire-5732Z kernel: [ 4082.206566] systemd-logind[987]: Operation finished.
Feb 10 20:23:49 waqas-Aspire-5732Z dbus[710]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.20" (uid=0 pid=1592 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=928 comm="NetworkManager ")
```

---

### Post by waqas-darkworks on 2015-02-14
I had TLP installed, removed TLP and the issue was resolved, needed something to save battery life so installed laptop-mode-tools but faced the same issue again, anybody knows whats going on?

---

