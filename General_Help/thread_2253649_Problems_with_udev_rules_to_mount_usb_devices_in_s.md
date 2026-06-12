---
title: "Problems with udev rules to mount usb devices in synchronized"
date: 2014-11-21
forum: General Help
---

### Post by Francisco_Marzoa on 2014-11-21
Hi there,

I am trying to write an udev rules file so all USB mass storage devices connected to my Ubuntu box are mounted synchronized, so they are written in real time instead of the usual way where, you know, the write is done to a buffer in memory and the OS flushes it whenever it wants, that quite often is while unmounting.

This is what I have done, so far:

/etc/udev/rules.d$ cat 10-usb-realtime-mount.rules 
SUBSYSTEMS="usb", ENV{mount_options}="realtime,sync"

It looks simple and straightforward, but it didn't work. For example, if I plug an USB key these are the options it uses when mounting:

/dev/sdg1 on /media/fran/FRANKEY type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

So it is ignoring my rule at all...

What am I doing wrong?

Thanks a lot in advance,

---

### Post by ajgreeny on 2014-11-21
> I am trying to write an udev rules file so all USB mass storage devices  connected to my Ubuntu box are mounted synchronized, so they are written  in real time instead of the usual way where, you know, the write is  done to a buffer in memory and the OS flushes it whenever it wants, that  quite often is while unmounting.Really?
If you try to unmount a USB while it is being written to the system tells you it can not be unmounted.

I think your problem may be more related to the slow write speed that many USB flash drives have.  The system puts the data to be copied to the USB into cache and then writes it as fast as the USB allows.  You should always eject or unmount a USB before removing it, so I can not see why you have this problem.

Perhaps I've misunderstood what you mean?

---

