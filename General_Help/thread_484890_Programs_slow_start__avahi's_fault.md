---
title: "Programs slow start : avahi's fault?"
date: 2007-06-26
forum: General Help
---

### Post by Ermanno on 2007-06-26
Hi everyone,
i've noticed that some applications like mc or vmware-server-console
start very very slow - without cpu load- but it takes 2-3 min (measured also with "time" )
to start mc for example...
i've discovered that is something related to avahi started by /etc/init.d/dbus at boot,
i'm running feisty kubuntu and this problem happened without installing nothing or changing my network configuration...

if i stop avahi all is fine but knetworkmanager can't work and some other applications too...

avahi/dbus and c. seems to run fine, configuration files are ok and /sbin/route and ifconfig are fine,

do u know what happened and how to fix it?

Thank you

---

