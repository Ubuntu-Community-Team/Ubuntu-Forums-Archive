---
title: "Zero DVD Playback"
date: 2007-01-17
forum: General Help
---

### Post by mbmccormick on 2007-01-17
Here's my problem- I don't have any DVD playback whatsoever. I can see the drive in nautilus in Computer, but once I insert a DVD into the drive it disappears. I have all the proper codecs and playback software. What am I doing wrong here? I am on edgy eft.

Here's my /etc/fstab...

proc              /proc     proc     defaults                                                       0       0
/dev/hda1      /           ext3     defaults,errors=remount-ro,data=writeback 	 0       1
/dev/hda5      none     swap     sw              				                 0       0
/dev/hdc        /media/cdrom   	udf,iso9660 	user,noauto     		       0       0



And my /etc/mtab...

/dev/hda1 / ext3 rw,errors=remount-ro,data=writeback 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-10-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

Any help is greatly appreciated. Thanks...

---

### Post by igknighted on 2007-01-17
You need to install the libdvdcss package in order to watch DVD movies.  Modern DVDs are encrypted and the4 libdvdcss package will allow Ubuntu to read them.  Just as a note, this is not entirely legal in the United States, but everyone uses it anyway as far as I know.

---

### Post by ardchoille42 on 2007-01-18
If you haven't installed it already, install libdvdread3. Then open your file manager and go to /usr/share/doc/libdvdread3/examples and run (with sudo) the install-css.sh script. that will fetch libdvdcss2 and install it for you. Then you should be able to view DVD movies in your media player.

---

### Post by mbmccormick on 2007-01-18
I have the libdvdread3 and libdvdcss3 (or 2 or whatever). All my libraries are up to date. I think its a mount issue because before I even open up a movie player, I cannot look at the drive. It dissapears... Any help???

---

