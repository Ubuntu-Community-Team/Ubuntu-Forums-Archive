---
title: "Which files to update after re-creating swap partition?"
date: 2014-10-16
forum: General Help
---

### Post by Kirkx on 2014-10-16
I have deleted the swap partition and then created a new one, which now has a different UUID. It seems that updating Grub2 does not update all files that need this new UUID and it has to be done manually. Beyond the two files listed below, are there any other files that need to be updated?

/etc/fstab

/etc/initramfs-tools/conf.d/resume

---

### Post by TheFu on 2014-10-16
just the fstab.

---

### Post by Alireza_Zamani on 2014-10-16
if you partition name is changed, edit rc.local
/etc/rc.local

---

### Post by ajgreeny on 2014-10-16
> **Alireza_Zamani said:**
> if you partition name is changed, edit rc.local
/etc/rc.local
I don't think that is needed, nor will it help.

You just need to edit /etc/fstab to update to the new UUID of swap, which you can find from command```
sudo blkid -c /dev/null
```

---

### Post by Kirkx on 2014-10-16
1) I think in this file UUID was actually automatically changed after reboot.
```
/etc/fstab
```

2) This file had an old UUID which didn't match any of my partitions.
```
/etc/initramfs-tools/conf.d/resume
```

3) ```
/etc/rc.local
```

This file only contains the following script:

```

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

exit 0

```

---

### Post by Alireza_Zamani on 2014-10-16
if you want set swap partition for next Boot you need add swap partitions in rc.local .
for example :

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


[B]swapon /dev/sda2
swapon /dev/sda4[/B]


exit 0



and this problem not related to GRUB !

---

### Post by ajgreeny on 2014-10-16
The /etc/fstab file would never update itself automatically as far as I'm aware, and in the past I have never ever needed to do more than edit the /etc/fstab file with the new UUID, so I am not aware of any need for the changes Alireza speaks of.  It is also worth stating that is no need for more than one swap partition even if you have many Linux OSs on your machine; you can simply add the one swap you have to each OS's fstab file.

Is swap working at the moment? Show the output of command ```
free -m
``` and we can see your swap size and current use.  Let's also see the output of ```
sudo blkid -c /dev/null
cat /etc/fstab
```

---

