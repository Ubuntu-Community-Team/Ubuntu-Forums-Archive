---
title: "Mounting Encrypted Partition Fails"
date: 2007-03-02
forum: General Help
---

### Post by judgekaster on 2007-03-02
I posted this same information on [launchpad]("https://launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/88213") but is yet unresolved. I hope someone out there can help.

I have an external USB harddrive with two partitions luks encrypted. In dapper and edgy, these partitions will be automounted after asking for a password. In feisty herd4 (upgraded as of mar 3), ubuntu will ask for a password but will not mount them even if they were successfully luksOpen'ed, i.e. the devices are show in /dev/mapper/, e.g.

```
/dev/mapper/luks_crypto_e422b233-eb11-9901-v04e-hr5a991234a0
```

I did the debugging instructions found [here]("https://wiki.ubuntu.com/DebuggingRemovableDevices") with no apparent problem.

I tried using gnome-mount 
```

gnome-mount -vbd /dev/sdb1
gnome-mount -vbd /dev/sdb2
gnome-mount -vbd /dev/sdb3

```
/dev/sdb1 is a non-encrypted partition and is consistently mounted fine. However /dev/sdb2 and /dev/sdb3, do not always mount. During the times that mounting fails, I get the following messages/warnings:

```

gnome-mount 0.5
libhal-storage.c 1401 : INFO: called LIBHAL_FREE_DBUS_ERROR but dbusError was not set.
** (gnome-mount:7037): DEBUG: Crypto volume - UDI '/org/freedesktop/Hal/devices/volume_uuid_5dfd5a12_e5a4_4b01_9b61_2e1805e432ae'
** (gnome-mount:7037): DEBUG: Setting up /org/freedesktop/Hal/devices/volume_uuid_5dfd5a12_e5a4_4b01_9b61_2e1805e432ae for crypto
Setup clear-text device for /dev/sdb2.
** (gnome-mount:7037): DEBUG: Waiting for cleartext volume backed by /org/freedesktop/Hal/devices/volume_uuid_5dfd5a12_e5a4_4b01_9b61_2e1805e432ae..
** (gnome-mount:7037): WARNING **: Timeout for waiting for cleartext device... Exiting.

```

I hope someone can help.

---

### Post by judgekaster on 2007-03-05
bump! any help?

---

