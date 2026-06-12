---
title: "How to permanently change permissions?"
date: 2015-10-01
forum: General Help
---

### Post by nathanhurley on 2015-10-01
Hi. I wanted to permanently change permission to "chmod 777" /dev/ttyUSB0". 

How do I do it so it's always set to that, so if I reboot I don't have to type that??

Thanks!!!

---

### Post by mikewhatever on 2015-10-01
You can add the command to /etc/rc.local, the command is then run on every boot. There is no way to permanently change it, as I don't think /dev/ttyUSB0 exists before the system is booted.

---

### Post by nathanhurley on 2015-10-02
Is This right? It doesn't seem to work...


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
chmod 777 /dev/ttyS0
chmod 777 /dev/tty/USB0




exit 0

---

