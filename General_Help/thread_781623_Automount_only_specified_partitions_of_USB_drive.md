---
title: "Automount only specified partitions of USB drive"
date: 2008-05-04
forum: General Help
---

### Post by 7marius on 2008-05-04
You've got an USB drive containing several partitions, you don't want all of them to mount automatically, here the solution:

1. Change udev rules as follows:
```
$ diff /var/backups/60-persistent-storage.rules /etc/udev/rules.d/60-persistent-storage.rules
24c24
< ENV{DEVTYPE}=="partition", IMPORT{parent}="ID_*"
---
> ENV{DEVTYPE}=="partition", IMPORT{parent}="ID_*", RUN+="/root/bin/usb_mount", ENV{REMOVE_CMD}="/root/bin/usb_unmount"
```

2. Create the mount script /root/bin/usb_mount:
```
#!/bin/sh
#
# Script to automatically mount specific partitions of USB drives with udev
#
# Feel free to modify and share under the GNU GPL v3
# Author: marius dot reiner at hdev dot de
#

[ "$ACTION" = "add" -a "${DEVTYPE}" = "partition" -a "$ID_BUS" = "usb" ] || exit 0

# Get uuid of current device
DEVUUID=`/sbin/vol_id -u ${DEVNAME}`

# Exit if no ID is available
if [ -z ${DEVUUID} ] ; then
   exit 0
fi

# Mount partition if entry in fstab is found
if [ -n "`/bin/grep -e \"^UUID=${DEVUUID}\" /etc/fstab`" ] ; then
   /bin/mount "UUID=${DEVUUID}"
fi
```

3. In case you need it, create an unmount script.

4. Find out the UUID of the partition you want to automount:
```
/sbin/vol_id -u /dev/<yourdevice>
```

4. Create an entry in /etc/fstab for each partition you want to automount ("users" allows all users to unmount it, which is useful because root will run the script, while you might want to unmount before pulling the plug as normal user):

```
UUID=<your-uuid> /media/usbstore reiserfs users,defaults 0 0
```

5. You probably have to switch off automount by "hald" for your drive first. I didn't find the GUI option, so I created this policy file:
```
$ cat /etc/hal/fdi/policy/disableusbautomount.fdi
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="storage.serial" string="HTS42121[...]">
      <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      <merge key="volume.policy.should_mount" type="bool">false</merge>
    </match>
  </device>
</deviceinfo>
```

Here you put the storage.serial you get from lshal.

Please let me know if you find a better solution or have any suggestions.

Regards,
Marius

---

