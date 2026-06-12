---
title: "rc.local entries not running at bootup"
date: 2013-07-06
forum: General Help
---

### Post by Hungry Man on 2013-07-06
My entries in rc.local won't startup. I've tried adding # in front of !/bin/sh -e, and removing it. No idea what's wrong.

> !/bin/sh -e#
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


gtk-redshift
gtk-redshift


mkdir /run/dnscrypt
dnscrypt-proxy --daemonize --user=dnscrypt
iptables-restore < /etc/iptables.rules


exit 0

edit: needed to writ efull path to the executables i guess.

---

