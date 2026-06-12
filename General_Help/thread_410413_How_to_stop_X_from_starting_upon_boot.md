---
title: "How to stop X from starting upon boot?"
date: 2007-04-15
forum: General Help
---

### Post by WebChat006 on 2007-04-15
I modified my xorg.conf file, only to find that as soon as X starts, my computer displays a blank screen and does not respond at all (Caps Lock key does not activate light and pressing Ctrl-Alt F1 does not take me to console.) Since I made a backup of xorg.conf, I just need to stop X from starting upon boot so I can replace it with the backup. However, my computer is  set to startx in the normal boot process, so how can I stop this?

---

### Post by kerry_s on 2007-04-15
I think you should use /etc/rc.local

sudo gedit /etc/rc.local

#!/bin/sh
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

rm /etc/X11/xorg.conf &
cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf &

exit 0


This will remove xorg.conf and copy your new one in it's place at system startup, so you don't have to drop to command-line to do it manually.

---

### Post by zekopeko on 2007-04-15
try the recovery mode when booting. beware that you are doing since you will be root

---

### Post by WebChat006 on 2007-04-15
Thank you zekopeko. Booting into recovery mode allowed me to recover (hehe) my xorg.conf backup.

---

