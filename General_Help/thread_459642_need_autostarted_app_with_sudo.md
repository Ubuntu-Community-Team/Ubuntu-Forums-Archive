---
title: "need autostarted app with sudo"
date: 2007-05-30
forum: General Help
---

### Post by malfist on 2007-05-30
How can I run a command that needs sudo at startup? As in sudo ifup wlan0?

---

### Post by kerry_s on 2007-05-30
put the command in /etc/rc.local

sudo gedit /etc/rc.local

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

ifup wlan0 &

exit 0

---

### Post by TH3_D0ct0R on 2007-05-30
idk if this would be the same but i want to have an icon be run in root

---

