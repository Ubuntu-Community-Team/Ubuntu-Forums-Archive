---
title: "udev rule won't execute RUN command"
date: 2008-03-24
forum: General Help
---

### Post by m4dm4n on 2008-03-24
Hi all,

I've been over and over this again but I can't see why this udev rule doesn't work. I'm trying to create a rule to auto-mount my iPod Touch using sshfs over WiFi when I plug it in to the USB cable. The NAME component is fine, a /dev node is created for "ipod". The output for udevtest is:

```
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/etc/udev/rules.d/00-init.rules' as rules file
parse_file: reading '/etc/udev/rules.d/05-options.rules' as rules file
parse_file: reading '/etc/udev/rules.d/10-local.rules' as rules file
parse_file: reading '/etc/udev/rules.d/20-names.rules' as rules file
parse_file: reading '/etc/udev/rules.d/30-cdrom_id.rules' as rules file
parse_file: reading '/etc/udev/rules.d/40-permissions.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-hplip.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libgphoto2.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libnjb.rules' as rules file
parse_file: reading '/etc/udev/rules.d/45-libsane.rules' as rules file
parse_file: reading '/etc/udev/rules.d/50-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/etc/udev/rules.d/55-hpmud.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-libpisock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/60-symlinks.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-input.rules' as rules file
parse_file: reading '/etc/udev/rules.d/65-persistent-storage.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/etc/udev/rules.d/80-programs.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-alsa.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-hwclock.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-ifupdown.rules' as rules file
parse_file: reading '/etc/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/etc/udev/rules.d/90-modprobe.rules' as rules file
parse_file: reading '/etc/udev/rules.d/95-hal.rules' as rules file
parse_file: reading '/etc/udev/rules.d/99-udevmonitor.rules' as rules file
parse_file: reading '/etc/udev/rules.d/libmtp.rules' as rules file
import_uevent_var: import into environment: 'MAJOR=189'
import_uevent_var: import into environment: 'MINOR=533'
import_uevent_var: import into environment: 'DEVTYPE=usb_device'
import_uevent_var: import into environment: 'DRIVER=usb'
import_uevent_var: import into environment: 'PHYSDEVBUS=usb'
import_uevent_var: import into environment: 'PHYSDEVDRIVER=usb'
import_uevent_var: import into environment: 'DEVICE=/proc/bus/usb/005/022'
import_uevent_var: import into environment: 'PRODUCT=5ac/1291/1'
import_uevent_var: import into environment: 'TYPE=0/0/0'
import_uevent_var: import into environment: 'BUSNUM=005'
import_uevent_var: import into environment: 'DEVNUM=022'
main: looking at device '/devices/pci0000:00/0000:00:10.4/usb5/5-3' from subsystem 'usb'
udev_rules_get_name: rule applied, '5-3' becomes 'ipod'
udev_db_get_device: found a symlink as db file
udev_device_event: device '/devices/pci0000:00/0000:00:10.4/usb5/5-3' already in database, cleanup
udev_node_add: creating device node '/dev/ipod', major=189, minor=533, mode=0660, uid=0, gid=0
main: run: 'su greg -c '/usr/bin/sshfs -o workaround=rename root@192.168.1.70:/var/root/Media /media/ipod''
main: run: 'socket:/org/freedesktop/hal/udev_event'
main: run: 'socket:/org/kernel/udev/monitor'
```

The rule I've created is in 10-local.rules and is as follows:
```
SUBSYSTEM=="usb", ATTR{idProduct}=="1291", ATTR{idVendor}=="05ac", NAME="ipod", RUN+="su greg -c '/usr/bin/sshfs -o workaround=rename root@192.168.1.70:/var/root/Media /media/ipod'"
```
The command added to the RUN list works fine when I execute it from the command line as root, which I assume is what the udev user is doing, but it doesn't execute when I actually connect the device, although the rule applies the NAME attribute fine.

Anything obvious I'm missing here? Is there some way to debug the RUN commands to work out at least what the result of trying to execute it is?

Any help would be much appreciated.

---

### Post by m4dm4n on 2008-03-24
Worked it out. For anyone struggling with this problem, you must use the full path to all executables you want to use. Naturally this includes "su" which I was trying to call to execute the command as my user account. The corrected rule is:
```
SUBSYSTEM=="usb", ATTR{idProduct}=="1291", ATTR{idVendor}=="05ac", NAME="ipod", RUN+="/bin/su greg -c '/usr/bin/sshfs -o workaround=rename root@192.168.1.70:/var/root/Media /media/ipod'"
```

---

