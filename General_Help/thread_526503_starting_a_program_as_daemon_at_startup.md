---
title: "starting a program as daemon at startup"
date: 2007-08-15
forum: General Help
---

### Post by SSCUltima on 2007-08-15
I want to start squid as a daemon when the system boots, im using 7.04 server. thanks

---

### Post by dougfractal on 2007-08-15
from [http://ubuntuforums.org/showthread.php?t=246791](http://ubuntuforums.org/showthread.php?t=246791)

> If you installed them using apt/synaptic they'll probably start at boot anyway. You can check by running

[QUOTE]ls -la /etc/rc3.d # (rc5.d if you have a GUI running) 
and you should see a list of service names like this:
S90shorewall@ S12syslog@ S20laptop-mode@ S56rawdevices@ S95kheader@
S03iptables@ S13partmon@ S20xfs@ S56xinetd@ S99local@
S04acpi@ S14acpid@ S25netfs@ S75keytable@
S04pcmcia@ S15cups@ S30dm@ S80freshclam@
S10network@ S17alsa@ S55sshd@ S85vpnclient_init@
S11portmap@ S18sound@ S56ntpd@ S90crond@

Anything starting with K is disabled and anything starting with S will run at bootup.[/QUOTE]

---

