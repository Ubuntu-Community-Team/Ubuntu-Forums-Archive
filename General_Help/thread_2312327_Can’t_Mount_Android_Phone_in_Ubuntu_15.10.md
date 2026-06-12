---
title: "Can’t Mount Android Phone in Ubuntu 15.10"
date: 2016-02-03
forum: General Help
---

### Post by AlexStargazer on 2016-02-03
Dear Forum:

I’ve been trying to mount my Sony Xperia Z3 Compact using mtp, but to no avail. When I connect the phone with its usb cable, nautilus prompts me to open an external media with the phone’s serial number. Unfortunately, it refuses to actually mount; and if I try right click > mount, it gives me the error message ‘Unable to open MTP device '[usb:001,010]'’. The phone, for the record, vibrates when it does this.

Using mtp-detect gives me:

```

libmtp version: 1.1.9

Listing raw device(s)
Device 0 (VID=0fce and PID=01bb) is a SONY Xperia Z3 Compact MTP.
   Found 1 device(s):
   SONY: Xperia Z3 Compact MTP (0fce:01bb) @ bus 1, dev 10
Attempting to connect device(s)
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
LIBMTP PANIC: failed to open session on second attempt
Unable to open raw device 0
OK.

```

Trying to connect it with mtp-connect:

```

libmtp version: 1.1.9

Device 0 (VID=0fce and PID=01bb) is a SONY Xperia Z3 Compact MTP.
ignoring libusb_claim_interface() = -6PTP_ERROR_IO: failed to open session, trying again after resetting USB interface
LIBMTP libusb: Attempt to reset device
ignoring libusb_claim_interface() = -6LIBMTP PANIC: failed to open session on second attempt
No devices.


```

Again, no cigar.

Does anyone know why my phone won’t mount? I’ve read that MTP is supposed to be supported and working…

(Also, before you ask, yes I’ve tried using a different usb port.)

---

### Post by AlexStargazer on 2016-02-05
Does no-one know what might be the problem?

---

### Post by slickymaster on 2016-02-05
Have you already checked out [this thread]("http://ubuntuforums.org/showthread.php?t=2226702")?

---

### Post by AlexStargazer on 2016-02-05
> **slickymaster said:**
> Have you already checked out [this thread]("http://ubuntuforums.org/showthread.php?t=2226702")?

I&#8217;ve not seen it previously. I tried the instructions (sans step 5, which apparently isn&#8217;t necessary?) and it worked. For a bit. Now it&#8217;s back to the same. Any ideas?

EDIT: Occasionally, it almost works. But then it cuts out again.

---

### Post by slickymaster on 2016-02-05
Sorry, none. I just needed to install **gmtp** package to connect my Samsung Galaxy S3 to my Xubuntu box.

---

### Post by gordintoronto on 2016-02-05
With Xubuntu 15.10, I plug in my Moto G to charge it, and it also appears on my desktop like a flash drive. Android 5.1. I can move files around as much as I want.

---

### Post by AlexStargazer on 2016-02-06
> **gordintoronto said:**
> With Xubuntu 15.10, I plug in my Moto G to charge it, and it also appears on my desktop like a flash drive. Android 5.1. I can move files around as much as I want.

I&#8217;ve got Android 5.11 also, but it doesn&#8217;t work. I wonder if it&#8217;s something on Sony&#8217;s side&#8212;the phone has given me nothing but trouble. The SD card randomly unmounts itself; sometimes without me even opening the charging flap. And when I go check the SD card, I find it connected in the card slot as if nothing were wrong. If I remove and re-insert the SD card, it frequently just gives me another &#8216;SD card unexpectedly removed&#8230;&#8217; message. Or it says &#8216;SD Card Removed,&#8217; despite the fact that I&#8217;ve inserted it again. (Or, it says &#8216;Checking SD card,&#8217; and then again, &#8216;SD card unexpectedly...&#8217;)

And the thing also has a setting that cannot be disabled: it beeps or vibrates whenever it catches or loses signal. The only way to turn it off is to put it on silent.

I&#8217;m going to try with some live distros to see if I can get it to work. If not, I think I&#8217;ll be returning it and telling everyone not to buy a Sony product. I certainly won&#8217;t make the same mistake again. 

As an aside: it mounts on Windows and OSX, weirdly enough.

EDIT: the phone mounts and I can copy files using a live Korora usb. This problem is definitely on Ubuntu&#8217;s side.

---

### Post by AlexStargazer on 2016-05-02
It&#8217;s working under 16.04. Thanks guys.

---

### Post by oygle on 2016-10-10
Running 16.04.1

I have installed all the 'mtp' software, as advised in other posts. I can connect USB cable and browse the phone (Samsung Galaxy S4), but I want to be able to **MOUNT** it.

Mount point is /media/mtp/phone and the permissions are 775

When I connect the cable and do this:

> $ **sudo mtpfs -o allow_other /media/mtp/phone**
[sudo] password for **********: 
Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 2, dev 2
Attempting to connect device
Listing File Information on Device with name: ******** (Galaxy S4)

but there is nothing showing in the folder /media/mtp/phone

If I try to access that path I get a msg "Could not enter folder /media/mtp/phone"

> $ **lsusb**
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0c45:670b Microdia 
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> $ **mount**
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4018560k,nr_inodes=1004640,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=807716k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=23,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda6 on /home type ext4 (rw,relatime,data=ordered)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/118 type tmpfs (rw,nosuid,nodev,relatime,size=807716k,mode=700,uid=118,gid=126)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=807716k,mode=700,uid=1000,gid=1000)
mtpfs on /media/mtp/phone type fuse.mtpfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)

> $ l**s -al /media/mtp/phone**
ls: cannot access '/media/mtp/phone': Transport endpoint is not connected

$ **ls -al /media/mtp/**
ls: cannot access '/media/mtp/phone': Transport endpoint is not connected
total 8
drwxrwxr-x 3 ******** ********* 4096 Oct 11 13:53 .
drwxr-xr-x 4 root  root  4096 Oct 11 13:53 ..
d????????? ? ?     ?        ?            ? phone

What do I need to change to be able to mount this mobile phone please ?

---

### Post by oygle on 2016-10-10
Running 16.04.1

I have installed all the 'mtp' software, as advised in other posts. I can connect USB cable and browse the phone (Samsung Galaxy S4), but I want to be able to **MOUNT** it.

Mount point is /media/mtp/phone and the permissions are 775

When I connect the cable and do this:

> $ **sudo mtpfs -o allow_other /media/mtp/phone**
[sudo] password for **********: 
Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 2, dev 2
Attempting to connect device
Listing File Information on Device with name: ******** (Galaxy S4)

but there is nothing showing in the folder /media/mtp/phone

If I try to access that path I get a msg "Could not enter folder /media/mtp/phone"

> $ **lsusb**
Bus 001 Device 006: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 0cf3:0036 Atheros Communications, Inc. 
Bus 001 Device 004: ID 0c45:670b Microdia 
Bus 001 Device 003: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

> $ **mount**
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4018560k,nr_inodes=1004640,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=807716k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=23,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/sda6 on /home type ext4 (rw,relatime,data=ordered)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
tmpfs on /run/user/118 type tmpfs (rw,nosuid,nodev,relatime,size=807716k,mode=700,uid=118,gid=126)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=807716k,mode=700,uid=1000,gid=1000)
mtpfs on /media/mtp/phone type fuse.mtpfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)

> $ l**s -al /media/mtp/phone**
ls: cannot access '/media/mtp/phone': Transport endpoint is not connected

$ **ls -al /media/mtp/**
ls: cannot access '/media/mtp/phone': Transport endpoint is not connected
total 8
drwxrwxr-x 3 ******** ********* 4096 Oct 11 13:53 .
drwxr-xr-x 4 root  root  4096 Oct 11 13:53 ..
d????????? ? ?     ?        ?            ? phone

What do I need to change to be able to mount this mobile phone please ?

---

### Post by hd.scania on 2016-12-01
```
hd_scania@HD-SCANIA:~$ su
Password:
root@HD-SCANIA:/home/hd_scania# apt install mtpfs go-mtpfs jmtpfs kio-mtp mtp-tools xmount libmtp9 libmtp-common libmtp-dev libmtp-runtime libmtp-dbg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libmtp-common is already the newest version (1.1.12-1).
libmtp-dbg is already the newest version (1.1.12-1).
libmtp-dev is already the newest version (1.1.12-1).
libmtp-runtime is already the newest version (1.1.12-1).
libmtp9 is already the newest version (1.1.12-1).
go-mtpfs is already the newest version (0.0~git20150802.0.3ef47f9-3).
jmtpfs is already the newest version (0.5-2).
kio-mtp is already the newest version (0.75+git20140304-2).
mtp-tools is already the newest version (1.1.12-1).
mtpfs is already the newest version (1.1-5).
xmount is already the newest version (0.7.3-1build1).
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
root@HD-SCANIA:/home/hd_scania# mtp-detect
libmtp version: 1.1.12


Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 2, dev 25
Attempting to connect device(s)
Android device detected, assigning default bug flags
Error 1: Get Storage information failed.
USB low-level info:
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 04e8
   idProduct: 6860
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Raw device info:
      Bus location: 2
      Device number: 25
      Device entry info:
         Vendor: Samsung
         Vendor id: 0x04e8
         Product: Galaxy models (MTP)
         Vendor id: 0x6860
         Device flags: 0x58008107
Configuration 0, interface 0, altsetting 0:
   Interface description contains the string "MTP"
   Device recognized as MTP, no further probing.
Device info:
   Manufacturer: samsung
   Model: SM-J700F
   Device version: 1.0
   Serial number: 3300a2b05098c2bd
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; android.com: 1.0;
   Detected object size: 64 bits
   Extensions:
        microsoft.com: 1.0
        android.com: 1.0
Events supported:
   0x4002
   0x4003
   0x4004
   0x4005
   0x4006
   0xc801
Device Properties Supported:
   0xd401: Synchronization Partner
   0xd402: Friendly Device Name
   0x5003: Image Size
   0x5001: Battery Level
Special directories:
   Default music folder: 0xffffffff
   Default playlist folder: 0xffffffff
   Default picture folder: 0xffffffff
   Default video folder: 0xffffffff
   Default organizer folder: 0xffffffff
   Default zencast folder: 0xffffffff
   Default album folder: 0xffffffff
   Default text folder: 0xffffffff
MTP-specific device properties:
   Friendly name: (NULL)
   Synchronization partner: (NULL)
   Battery level 86 of 100 (86%)
libmtp supported (playable) filetypes:
   Folder
   Text file
   HTML file
   RIFF WAVE file
   ISO MPEG-1 Audio Layer 3
   MPEG video stream
   JPEG file
   BMP bitmap file
   GIF bitmap file
   JFIF file
   Portable Network Graphics
   TIFF bitmap file
   Microsoft Windows Media Audio
   Ogg container format
   Advanced Audio Coding (AAC)/MPEG-2 Part 7/MPEG-4 Part 3
   MPEG-4 Part 14 Container Format (Audio+Video Emphasis)
   ISO MPEG-1 Audio Layer 2
   Abstract Playlist file
   XML file
   Free Lossless Audio Codec (FLAC)
OK.
root@HD-SCANIA:/home/hd_scania# lsusb
Bus 002 Device 005: ID 8086:0189 Intel Corp. 
Bus 002 Device 027: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 002 Device 026: ID 24ae:1100  
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1015 Silicon Motion 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@HD-SCANIA:/home/hd_scania# exit
hd_scania@HD-SCANIA:~$
```
```
#/etc/fuse.conf - Configuration file for Filesystem in Userspace (FUSE)


#Set the maximum number of FUSE mounts allowed to non-root users.
#The default is 1000.
#mount_max = 1000


#Allow non-root users to specify the allow_other or allow_root mount options.
user_allow_other
```
```
SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", MODE="0666", GROUP="plugdev"
```
```
# Samsung Galaxy Tab J7
# ATTR{idVendor}=="04e8", ATTR{idProduct}=="6860", SYMLINK+="libmtp-%k", ENV{ID_MTP_DEVICE}="1", ENV{ID_MEDIA_PLAYER}="1"
```
My first 5 steps are here and I have reset Udev and rebooted but Nautilus still dsnt see my phone.

---

