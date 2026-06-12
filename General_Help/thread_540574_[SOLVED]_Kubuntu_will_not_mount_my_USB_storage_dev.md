---
title: "[SOLVED] Kubuntu will not mount my USB storage devices"
date: 2007-09-01
forum: General Help
---

### Post by bogdan_5844 on 2007-09-01
i looked at other topics,but i couldn't find something similar...
oh well,here's how it goes:

Ubuntu 7.04 installed,i removed all GNOME software and all that i could find in Synaptic with the GNOME name and installed kubuntu-desktop.

Ok,all fine.but when I tried to connect my external hard disk to save some data,i noticed that ubuntu now doesn't mount it.the message "A new USB device has been detected" appears,but does no good.
This also appears with my PackardBell Pulse mp3 player

What can I do?Please help,i really need my external HDD :(

---

### Post by taurus on 2007-09-01
Can you mount it by hand, from a terminal?  Post

```
sudo fdisk -l
df -h
```

---

### Post by bogdan_5844 on 2007-09-01
wait,my mp3 player now works,i don't know how,but my hdd still doesnt
i don't know how to mount it by hand

the output from the 2 commands(hdd plugged in):

```
bodo@Bodo-PackardBell:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        3523     7815622+  82  Linux swap / Solaris
/dev/sda3            3524       19457   127989855   83  Linux

Disk /dev/sdb: 6144 MB, 6144284672 bytes
255 heads, 63 sectors/track, 747 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         746     5992213+   7  HPFS/NTFS
bodo@Bodo-PackardBell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             121G  7.0G  108G   7% /
varrun                443M  112K  443M   1% /var/run
varlock               443M     0  443M   0% /var/lock
procbususb            443M  120K  443M   1% /proc/bus/usb
udev                  443M  120K  443M   1% /dev
devshm                443M     0  443M   0% /dev/shm
lrm                   443M   33M  410M   8% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              20G  7.9G   12G  40% /media/sda1
bodo@Bodo-PackardBell:~$    
```

---

### Post by taurus on 2007-09-01
Try something like

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by bogdan_5844 on 2007-09-01
on the second command it gives this:

```
bodo@Bodo-PackardBell:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

```
i think that i have to format the drive in windows,eh?(i have an XP partition by the way)

---

### Post by taurus on 2007-09-01
It means that you need to boot back in XP, plug in your USB drive, and _then unmount_ it cleanly first.  Don't just unplug it from your machine.

Now, see if you can mount it with Ubuntu this time.

---

### Post by bogdan_5844 on 2007-09-02
did the safe removal thing in windows,manual mounting works,but the automatic one doesn't :(

---

### Post by bogdan_5844 on 2007-09-09
switched to GNOME,now works ;-)

---

