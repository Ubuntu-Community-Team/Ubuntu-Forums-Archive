---
title: "Udev rules boot errors"
date: 2013-05-15
forum: General Help
---

### Post by frinx on 2013-05-15
TL;DR; Udev is showing a lot of errors during boot and it is pointing to a .rules file.

A little background: I recently upgraded an Ubuntu 5 server to Ubuntu 12. I performed a stepwise upgrade to avoid what anyway happened. During all these upgrades the system completely crashed several times, requiring a Live CD and a lot of adding, removing and reinstalling of packages. In the end everything works again and the system boots (almost) normally.

Below are the errors that appear. They are non blocking errors, erything else works well and the system starts but I would like to resolve them. This started when the computer hanged while upgrading to 12.04 and had to be restarted. I fixed most of the errors with a live cd and apt-get install -f, remove, update, upgrade, dpkg...

The problem: It starts with the BUS errors:

```
udevd[xxx]: unknown key 'BUS' in /lib/udev/rules.d/020_permission.rules:x
udevd[xxx]: invalid rule '/lib/udev/rules.d/020_permission.rules:x'
```

After that I get a thousand (literally) lines of:

```
udevd[xxx]: failed to execute  '/sbin/udev_run_devd' '/sbin/udev_run_devd' : No such file or directory
```

There are a few errors like:

```
udevd[704]: kernel-provided name 'dm-0' and NAME= 'mapper/simlib-lv1' disagree, please use SYMLINK+= or change the kernel to provide the proper name

udevd[869]: kernel-provided name 'uinput' and NAME= 'input/uinput' disagree, please use SYMLINK+= or change the kernel to provide the proper name

udevd[xxx]: kernel provided name 'dm-0' and -NAME= '/dev/mapper/simlib-lv1' will not overwrite it

udevd[704]: device node '/dev/mapper/simlib-lv1' already exists, link to '/dev/mapper/simlib-lv1' will not overwrite it
```

I might also mention that I removed the package cups because it caused major errors. I did not try putting it back, but if I understood well that is used for printing. Also, after the upgrade to 12.04 crashed I had to reinstall udev.

Here is the rules file.. 020_permission.rules

```
# default permissions for block devices
SUBSYSTEM=="block",             GROUP="disk"
SUBSYSTEM=="block", SYSFS{removable}=="1",  GROUP="floppy"

# IDE devices
BUS=="ide", KERNEL=="hd[a-z]*", PROGRAM="/etc/udev/scripts/removable.sh %k", RESULT=="1", \
  MODE="0640", GROUP="plugdev"
BUS=="ide", KERNEL=="hd[a-z]", SYSFS{removable}="1", \
  PROGRAM="/bin/cat /proc/ide/%k/media", RESULT=="cdrom*",      MODE="0660", GROUP="cdrom"
BUS=="ide", KERNEL=="ht[0-9]*",                 GROUP="tape"
BUS=="ide", KERNEL=="nht[0-9]*",                GROUP="tape"

# SCSI devices
BUS=="scsi", SYSFS{type}=="1",  GROUP="tape"
BUS=="scsi", SYSFS{type}=="5",  GROUP="cdrom"
BUS=="scsi", SYSFS{type}=="6",  GROUP="scanner"
BUS=="scsi", KERNEL=="sd[a-z]*", PROGRAM="/etc/udev/scripts/removable.sh %k 'usb ieee1394'", RESULT="1", MODE="0640", GROUP="plugdev"

# USB devices
BUS=="usb", KERNEL=="legousbtower*", MODE="0666"
BUS=="usb", KERNEL=="lp[0-9]*", GROUP="lp"
BUS=="usb", KERNEL=="ub[a-z]*", NAME="%k", MODE="0640", GROUP="plugdev"

# serial devices
SUBSYSTEM=="tty",   GROUP="dialout"
SUBSYSTEM=="capi",  GROUP="dialout"
SUBSYSTEM=="slamr", GROUP="dialout"

# vc devices (all members of the tty subsystem)
KERNEL=="ptmx",     MODE="0666", GROUP="root"
KERNEL=="console",  MODE="0600", GROUP="root"
KERNEL=="tty",      MODE="0666", GROUP="root"
KERNEL=="tty[0-9]*",    GROUP="root"

# video devices
SUBSYSTEM=="video4linux", GROUP="video"
SUBSYSTEM=="drm",   GROUP="video"
SUBSYSTEM=="dvb",   GROUP="video"
SUBSYSTEM=="em8300",    GROUP="video"
SUBSYSTEM=="graphics",  GROUP="video"
SUBSYSTEM=="nvidia",    GROUP="video"

# misc devices
KERNEL=="random",   MODE="0666"
KERNEL=="urandom",  MODE="0444"
KERNEL=="mem",      MODE="0640", GROUP="kmem"
KERNEL=="kmem",     MODE="0640", GROUP="kmem"
KERNEL=="port",     MODE="0640", GROUP="kmem"
KERNEL=="full",     MODE="0666"
KERNEL=="null",     MODE="0666"
KERNEL=="zero",     MODE="0666"
KERNEL=="inotify",  MODE="0666"
KERNEL=="sgi_fetchop",  MODE="0666"
KERNEL=="sonypi",   MODE="0666"
KERNEL=="agpgart",  GROUP="video"
KERNEL=="nvram",    GROUP="nvram"
KERNEL=="rtc",      MODE="0660", GROUP="audio"

KERNEL=="cdemu[0-9]*",  GROUP="cdrom"
KERNEL=="pktcdvd[0-9]*", GROUP="cdrom"
KERNEL=="pktcdvd",  MODE="0644"

# printers and parallel devices
SUBSYSTEM=="printer",   GROUP="lp"
SUBSYSTEM=="ppdev", GROUP="lp"
KERNEL=="pt[0-9]*", GROUP="tape"
KERNEL=="pht[0-9]*",    GROUP="tape"

# sound devices
SUBSYSTEM=="sound", GROUP="audio"

# ieee1394 devices       
KERNEL=="raw1394",  GROUP="disk"
KERNEL=="dv1394*",  GROUP="video"
KERNEL=="video1394*",   GROUP="video"

# input devices
KERNEL=="event[0-9]*",  PROGRAM="/etc/udev/scripts/inputdev.sh %k", \
            RESULT=="inputdev", MODE="0664", GROUP="video"
KERNEL=="js[0-9]*", MODE="0664"

# AOE character devices
SUBSYSTEM=="aoe",           MODE="0220", GROUP="disk"
SUBSYSTEM=="aoe", KERNEL=="err",    MODE="0440"

```
I am not very experienced with linux, but also not a complete noob. I tried to provide as much info as possible. Please let me know if you need more info. After searching online, on this and other forums for possible fixes, I could not find anything. What can I do to fix this? Thank you.

---

### Post by tgalati4 on 2013-05-15
Normally, it is recommended to perform a clean install.  Especially when jumping so many releases.

It's possible that the name of udev script has changed:

tgalati4@Mint14-Extensa ~ $ ls -la /sbin/ud*
-rwxr-xr-x 1 root root 137248 Oct 11  2012 /sbin/udevadm
-rwxr-xr-x 1 root root 137312 Oct 11  2012 **/sbin/udevd**

Not **udev_run_devd** which does not exist on 12.10.  Not sure about 12.04.

Even if you clean up these errors and you get your machine to boot, would you trust it to run correctly as a server?

I would back up all of the important data on the server.  Wipe the disk and start with a clean install.

The fact that your machine crashed between upgrades is troubling.  Were these software issues or is the hardware failing?

---

### Post by frinx on 2013-05-15
Thank you for your answer. The machine boots and works properly. It isn't a critically important machine, rather an in-house dev server that we decided to revive. There was no option for a clean install because there was too much data to be reconfigured and moved back and forth.

What do you suggest I try? Change some script that looks in the wrong folder during boot up? Which one?
I currently don't have access to the machine so I can't confirm the folder change, but you are probably right.

---

### Post by tgalati4 on 2013-05-15
The errors suggest a fundamental problem with the udev system.  Now this could be broken because of the broken updates that occured.  Because the udev system is used to detect hardware and manage kernel events it is critical to pre and post installations scripts that happen as part of the package update process.

You can learn more about udev:

```
man udev
man udevd
man udevadm
```

If a server is running Breezy Badger (5.10--October 2005, now 7 1/2 years old) how important could it possibly be?  What prevents wiping the machine or pulling the hard disk and replacing it, keeping the old disk as a backup?  That way you would have a clean install of 12.04 then you can add the services that you need and migrate the data from the old disk.


This is not an easy fix.  Because of the questionable upgrade path taken, you may have bits and pieces of the old system(s) and that alone would take a lot of time to troubleshoot.

Try to reinstall udev with:

```
sudo apt-get purge udev
sudo apt-get install udev
```

---

