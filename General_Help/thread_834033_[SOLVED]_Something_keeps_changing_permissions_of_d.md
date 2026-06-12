---
title: "[SOLVED] Something keeps changing permissions of /dev/null /dev/urandom etc"
date: 2008-06-19
forum: General Help
---

### Post by heathd on 2008-06-19
Hi,

a few weeks ago I installed wvdial as I got a usb 3g mobile modem. This is all working fine.

However, since then strange things have been happening to items in /dev

In particular /dev/null /dev/urandom and several other devices are now appearing with the following permissions:

crw-rw----  1 root   dialout   1,   3 2008-04-25 17:15 null
crw-rw----  1 root   dialout   1,   8 2008-06-19 07:47 random
crw-rw----  1 root   dialout   1,   9 2008-06-19 07:48 urandom
crw-rw----  1 root   dialout   1,   5 2008-06-19 07:47 zero

Even if I change these e.g.:

$ chmod go+rw /dev/null

At some point the permissions get changed back again. I can't work out if this happens on reboot or by some cron job. It's really driving me crazy as some things do need to be able to read /dev/urandom and many scripts send output to /dev/null.

Any suggestions?

David

---

### Post by chrisccoulson on 2008-06-19
The files under /dev are volatile and re-created at boot time, which is why the permissions reset. The permissions are determined by UDEV rules in /etc/udev/rules.d. It is likely that something has added or changed some UDEV rules which is messing up the permissions, although I'm not sure how this has happened. Certainly the group ownership shouldn't be 'dialup' and /dev/null shouldn't have any read permissions whatsoever.

I can't help you further until I get home this evening really

---

### Post by heathd on 2008-06-19
Ok, I did have a poke around udev but don't really understand it. I've attached the contents of /etc/udev/rules.d

Of particular note is the ZTEMF622.rules file, which is for the 3g modem I have (manufacturer ZTE model MF622). Perhaps this has messed something up?

David

---

### Post by chrisccoulson on 2008-06-19
Hmmm, not entirely sure what is going on. ZTEMF622.rules looks a bit suspicious though and is setting some devices to GROUP="dialout" and MODE="660", which are the permissions and ownership you see. I'm not going to pretend I fully understand it though. What package does this file belong to? Try:
```
dpkg -S /etc/udev/rules.d/ZTEMF622.rules
```

---

### Post by heathd on 2008-06-19
```

$ dpkg -S /etc/udev/rules.d/ZTEMF622.rules
dpkg: /etc/udev/rules.d/ZTEMF622.rules not found.

```

I think maybe it gets put there by some hotplug or something? (another part of the system I don't really understand)

---

### Post by heathd on 2008-07-31
Ok, I finally found time to have another look at this and read the udev documentation, and I found a solution.

First, I think I got the ZTEMF622.rules file from another ubuntu forum thread (sorry I had forgotten). That thread is here:

[http://ubuntuforums.org/showthread.php?t=665332](http://ubuntuforums.org/showthread.php?t=665332)

using udevtest, I was able to check what permissions were getting assigned for things such as /dev/null:

```
$ udevtest /sys/devices/virtual/mem/null

...
udev_node_add: creating device node '/dev/null', major=1, minor=3, mode=0660, uid=0, gid=20
...

```

Notice that the gid is 20, ie incorrectly using 'dialout'.

Here's the original ZTEMF622.rules file:
```

ACTION!="add", GOTO="ZTE_End"

# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000", SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"

# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001", SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"

LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
RUN+="/usr/sbin/usb_modeswitch -d 1 -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x0001"

LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"

LABEL="ZTE_End"

```

I couldn't find in the udev documentation any description of the GOTO command. Suspecting the MODE/GROUP line, I changed from:

```

MODE="660", GROUP="dialout"

```

to:

```

SUBSYSTEM=="usb", SYSFS{idProduct}=="0001", SYSFS{idVendor}=="19d2", MODE="660", GROUP="dialout"

```

Which cleared up the problem. I guess the MODE and GROUP rules apply globally, even if they are used in a GOTO block, so they need the constraint specifying the device type etc.

Hope this helps other users of the ZTE MF622 Usb modem. Is anyone aware of a any central resource or wiki page where I should add this info?

David

---

