---
title: "Usb mounted as read-only after suspend"
date: 2008-03-18
forum: General Help
---

### Post by locoocol on 2008-03-18
Hi, first I will confess that i am a linux noob

Im having troubles with my eeepc mod (usb hub + 4gb datatraveler + bluetooth inside case). On boot everything works like a charm, the usb mounts as /home as I've configured during the instalation (8.04 alpha 6). But when I return from a Suspend, the drive seems to return as a read-only device. I cannot write o create folders on my user Home folder. 

Ive read similar issues solved but with fat partitions.

Please help me figuring out this,

These are my Fstab, Mtab and the 01-***.rule created to always mount the pendrive in the same position.

My FSTAB

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc124318-7b33-47e1-ab82-68c8cc6f982a /               ext3    noatime,defaults,errors=remount-ro 0       0
# /dev/sdc1
# UUID=5a32cf9c-a43c-4ef8-9c8d-08d866d15024 /home           ext3  noatime,defaults,errors=remount-ro        0       0
/dev/usf    /home           ext3    rw,defaults,noatime        0       0

tmpfs     /var/log       tmpfs     defaults,noatime        0 0
tmpfs     /tmp              tmpfs     defaults,noatime        0 0
tmpfs     /var/tmp       tmpfs     defaults,noatime        0 0
```

THE RULE (/etc/udev/rules.d/01-ina.rules):
```


# Rules to ensure USB storage devices have persistent names and are mounted
# at boot.

# USB FIXED
BUS=="usb", KERNEL=="sd*", SYSFS{serial}=="89900000000000000000007C", NAME="usf", OPTIONS+="last_rule", RUN+="/bin/mount /dev/usf"
```

THE MTAB:
```


/dev/sda1 / ext3 rw,noatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-12-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/usf /home ext3 rw,noatime 0 0
```

---

### Post by locoocol on 2008-03-19
bump

---

### Post by locoocol on 2008-03-19
Update,,, I`ve made some small adjustments but I still get the same result, the pendrive is still readonly after resume remount.

PLEASE I NEED A HAND! its driving me insane

These are the changes (in bold)

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc124318-7b33-47e1-ab82-68c8cc6f982a /               ext3    noatime,defaults,errors=remount-ro 0       0
# /dev/sdc1
# UUID=5a32cf9c-a43c-4ef8-9c8d-08d866d15024 /home           ext3  noatime,defaults,errors=remount-ro        0       0
/dev/usf    /home           ext3    **rw,users,auto,noatime**        0       0

tmpfs     /var/log       tmpfs     defaults,noatime        0 0
tmpfs     /tmp              tmpfs     defaults,noatime        0 0
tmpfs     /var/tmp       tmpfs     defaults,noatime        0 0
```

THE RULE (/etc/udev/rules.d/01-ina.rules):
```


# Rules to ensure USB storage devices have persistent names and are mounted
# at boot.

# USB FIXED
BUS=="usb", KERNEL=="sd*", SYSFS{serial}=="89900000000000000000007C", NAME="usf", OPTIONS+="last_rule", RUN+="/bin/mount /dev/usf **/home -o rw,users,noatime,auto**"
```

---

### Post by locoocol on 2008-03-19
Problem Solved, after reading the complete udev guide I finally found a way. The guide can be found [here]("http://reactivated.net/writing_udev_rules.html").

The problem was solved by changing the udev rule. I leave you both fstab and 01-ina.rule

01-ina.rule:
```

# Rules to ensure USB storage devices have persistent names and are mounted
# at boot.

# USB FIJO 
BUS=="usb", KERNEL=="sd*", ATTRS{serial}=="89900000000000000000007C", SYMLINK+="usf", MODE="0666", OPTIONS+="last_rule", RUN+="/bin/mount /dev/usf"

```

Fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc124318-7b33-47e1-ab82-68c8cc6f982a /               ext3    noatime,defaults,errors=remount-ro 0       0
# /dev/sdc1
# UUID=5a32cf9c-a43c-4ef8-9c8d-08d866d15024 /home           ext3    noatime,defaults,errors=remount-ro        0       0
/dev/usf	/home           ext3    rw,users,noatime        0       0

tmpfs     /var/log       tmpfs     defaults,noatime        0 0
tmpfs     /tmp              tmpfs     defaults,noatime        0 0
tmpfs     /var/tmp       tmpfs     defaults,noatime        0 0

```

---

### Post by chrisccoulson on 2008-03-20
Hi, I've just noticed that you set permissions on /dev/usf to 0666 with your UDEV rule. This means that a normal user could write data to the raw block device without sudo (using something like dd), which could cause bad filesystem corruption. You might want to fix that if your machine is used by more than one user.

---

### Post by locoocol on 2008-03-20
You are right, i know i should probably change the permissions to 0660. I will test those permissions with a clean install of 8.04 beta,,,, so im waiting the release today.

Thanks for your input

---

