---
title: "udev rule not started during boot"
date: 2014-08-01
forum: General Help
---

### Post by Richard_Klingler on 2014-08-01
Hello...first time here and already a strange problem...

I added a custom rule as /etc/udev/rules.d/99-agilent-82357b-gpib.rules 
to change deive permission and startup a configuration program for a USB GPIB adapter:



```
ATTRS{idVendor}=="0957", ATTRS{idProduct}=="0718", RUN+="/usr/local/bin/gpib.sh"

```

But this rule only gets applied after boot when I replug the USB adapter, or if I trigger it manually with "sudo udevadm trigger".


The original rule was:

```
ATTRS{idVendor}=="0957", ATTRS{idProduct}=="0718", RUN+="RUN+="/bin/chown root:gpib /dev/gpib*; /bin/chmod 660 /dev/gpib*; /usr/local/sbin/gpib_config"

```

But that didn't run at all, as I found out it didn't like the "*" character in the line...
So put those command into the exernal shell script located under "/usr/local/bin/gpib.sh"


Something to do with the filesystme not ready during boot or not accessible?
Syslog and udev log don't show any error/warning messages...

---

