---
title: "how to skip grub countdown"
date: 2017-07-08
forum: General Help
---

### Post by unityforever on 2017-07-08
i have windows.
and grub will count 10 seconds for selecting while booting.
i set grub TIMEOUT=0 then update it.
but it still counts 10...
if i set TIMEOUT=3 and update
it would be 3...

---

### Post by ajgreeny on 2017-07-08
It is always necessary to run ```
sudo update-grub
``` after making changes in **/etc/default/grub** and from what you have said it is not totally clear if you did this or not.

Have you read [https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup) in detail, particularly the [Grub2 Setup section about /etc/default/grub]("https://help.ubuntu.com/community/Grub2/Setup#A.2Fetc.2Fdefault.2Fgrub")

---

### Post by gjohnz on 2017-07-08
Perhaps there is a spelling error?
```
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=#ff0000]GRUB_TIMEOUT=10[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=true
```

---

### Post by Keith_Helms on 2017-07-08
How do you want it to work?  Do you want it to boot the default OS immediately without any countdown or do you want it to wait forever until you select an OS?   The grub script /etc/grub.d/30_os-prober overrides a timeout value of 0 and sets it to 10 instead.  Disabling the timeout completely would probably require manually editing that script, which is not recommended and any change would likely be wiped out whenever the grub package got updated.  If you want it to wait forever, you can enter GRUB_TIMEOUT=-1.

Update:

If you REALLY want to make the timeout go away and immediately boot the default OS, you can add the following script into the /etc/grub.d directory

```

#! /bin/sh
set -e

echo "timeout set to ${GRUB_TIMEOUT}" >&2
cat << EOF
set timeout=${GRUB_TIMEOUT}
EOF

```

Name it 31_set-timeout so that it will get executed after the 30_os-prober script which overrides 0 seconds back to 10 and don't forget to make it owned by root and executable.
```

sudo chown root:root 31_set-timeout
sudo chmod +x 31_set-timout

```
With this script, if you set GRUB_TIMEOUT=0 in /etc/default/grub, it REALLY will boot the default OS without displaying a menu.  I have given you the tool to shoot yourself in the foot.  If your default OS becomes unbootable for some reason, your only option will probably be to boot from a recovery disc.

---

