---
title: "RC.Local"
date: 2014-05-27
forum: General Help
---

### Post by chazzyfresh33 on 2014-05-27
I'm attempting to implement the SSD improvements described in this website ([https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)) via the RC local file. Since I don't have much experience with this I want to make sure I'm doing it right by getting a second set of eyes on it. Does this look right to everyone?

Also, how can I tell it's running once I've saved it?

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
#
# Modification for SSD
for dir in apparmor apt cups dist-upgrade fsck gdm installer samba unattended-upgrades ; 
do
           if [ ! -e /var/log/$dir ] ; then
                   mkdir /var/log/$dir
           fi
done
fstrim -v /
iwconfig wlan0 txpower 5
exit 0

---

### Post by computertip on 2014-05-28
Looks OK. You can't tell whether the added code in rc.local is running or not, simply because this is only a set of commands that are being executed at booting. So it's not an active process or something like that. :)

rc.local can be compared to autoexec.bat in Windows / MS-DOS.

---

### Post by chazzyfresh33 on 2014-05-29
Thanks!

---

