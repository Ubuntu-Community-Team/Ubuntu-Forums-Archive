---
title: "usb permissions"
date: 2007-02-08
forum: General Help
---

### Post by joker on 2007-02-08
I have an iRiver IFP-895 music player which I can access only if I start ifpgui as root.   Please tell me how I can have this device mount without needing to be root.  Thank you.

lsusb says:
Bus 003 Device 010: ID 4102:1008 iRiver, Ltd. iFP-800 series mp3/ogg vorbis player

---

### Post by taurus on 2007-02-08
How about the output of this command?

```
mount
```

---

### Post by joker on 2007-02-09
/mount 

proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/hda1 on /media/hda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda5 on /media/hda5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/hda6 on /media/hda6 type ext3 (rw)
/dev/hdb1 on /media/music type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

---

### Post by RDiamond on 2007-02-20
I have an iFP-795 and had the same problem. After serching the net, I found the following:

1. Create a file in /etc/udev/rules.d
    I called it "ifpdev.rules"

2. file should contain the following:

# udev rules file for supported ifp devices
#
# To add an USB ifp device, add a rule to the list below between the SUBSYSTEM...
# and LABEL... lines.
#
# To run a script when your ifp is plugged in, add RUN="/path/to/script"
# to the appropriate rule.
#

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libifp_rules_end"

# ifp-1xx
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1001", GROUP="plugdev"
# ifp-3xx
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1003", GROUP="plugdev"
# ifp-5xx
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1005", GROUP="plugdev"
# ifp-7xx
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1007", GROUP="plugdev"
# ifp-8xx
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1008", GROUP="plugdev"
# ifp-9xx
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1009", GROUP="plugdev"
# ifpdev
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1010", GROUP="plugdev"
# The N10
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1011", GROUP="plugdev"

LABEL="libifp_rules_end"

3. Restart the system (so udev restarts with new rules).

This has worked great for me. I can now access my device under my normal logon.

---

### Post by mhenry676 on 2007-10-29
DUDE! THANK YOU!

Got my iRiver IFP-780 working in Kubuntu Gutsy 7.10 thanks to your script! Easier anyway.

I did have to add the group plugdev to my starting user, but good to go!

:guitar:

---

