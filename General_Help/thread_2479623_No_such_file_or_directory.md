---
title: "No such file or directory"
date: 2022-09-30
forum: General Help
---

### Post by raleigh3 on 2022-09-30
This is really frustrating.

The directory exists.

How do I fix this?

```
cd: /media/andy/5b4b2ae5-9aaa-4559-9f41-afb313998c75/home/andy/bin/: No such file or directory
Thunar: Failed to open "/media/andy/5b4b2ae5-9aaa-4559-9f41-afb313998c75/home/andy/bin/": Error when getting information for file “/media/andy/5b4b2ae5-9aaa-4559-9f41-afb313998c75/home/andy/bin”: No such file or directory

```

---

### Post by TheFu on 2022-09-30
I had an issue like that a few hours ago. Seems my USB/eSATA device power decided to shut down.  It is an old, external, array. Very cheap.  The power button is logical, not physical, so when there's any power hit (which didn't happen), the power will be off and remain off. Sigh.

Cycled the power for the device and ran 'sudo mount -a' to get the fstab entries to remount everything not already mounted.  I don't allow gvfs on my systems.  That mount location for your issue is clearly a gio/gvfs location.  At least give the partition a label (use gparted), so that ugly UUID isn't involved in the mount.  Humans understand 'labels' much easier, after all.  I doubt I could convince you to use 'autofs' for all your USB device mounts., but that really is the best solution for USB storage.  

Prefer SAS, SATA, eSATA or infiniband storage over USB connections.  USB connections are prone to becoming loose due to vibrations. Those other connection types of screws or latches to hold them in  place.  Connections matter.  Plus the USB-storage protocol really sucks compared to the SATA protocol.

Of course, it could be a number of other issues. Check the cable and power supply first.   'dmesg' often has disconnect errors when storage 'disappears'.  Once you get the connection back, check the disk using smartctl for any large issues.

BTW, support for Ubuntu Mate 18.04 ended in Apr 2021.

---

### Post by raleigh3 on 2022-09-30
I still have a few years.

```
Support status summary of '7':

You have 1991 packages (66.9%) supported until April 2023 (Canonical - 5y)

You have 5 packages (0.2%) that can not/no-longer be downloaded
You have 981 packages (33.0%) that are unsupported

Your Hardware Enablement Stack (HWE) is supported until April 2023.
```

---

### Post by raleigh3 on 2022-09-30
It is not a hardware issue.

Touching a file seems to have solved the problem.

```
touch /media/andy/5b4b2ae5-9aaa-4559-9f41-afb313998c75/home/andy/bin/status.sh
thunar /media/andy/5b4b2ae5-9aaa-4559-9f41-afb313998c75/home/andy/bin/
```

---

### Post by TheFu on 2022-09-30
> **raleigh3 said:**
> I still have a few years.

```
Support status summary of '7':

You have 1991 packages (66.9%) supported until April 2023 (Canonical - 5y)

You have 5 packages (0.2%) that can not/no-longer be downloaded
You have 981 packages (33.0%) that are unsupported

Your Hardware Enablement Stack (HWE) is supported until April 2023.
```

I think you're looking for good news, not the bad news.

```
You have  **981 packages (33.0%) that are unsupported**
```
So, 1/3rd of the packages - mostly tied to Mate and GUI programs aren't supported anymore.  The "core" ubuntu stuff that is shared with Server and the Gnome3 DE will keep support.

Use 
```
ubuntu-support-status --show-unsupported
```
to see the bad news.  Anything with a network aspect is a concern.  Use virtualization?  Ouch.  All the mate-* packages are clearly NOT supported.  

Anyway, your choice. Just providing the information, so you can decide the risks for yourself.  

I'm moving my 18.04 servers to 20.04 now, as workload allows.  Did one last weekend. Choose to do a fresh install, but a few things are still unsolved. Most things migrated (used my backup+restore methods) to backup the 18.04 stuff, but restore it to a 20.04 fresh install.  

Skipped 18.04 desktop stuff on my main desktop by doing 16.04 --> 20.04.  That was painful and ended up having to reload the OS about a month later due to odd problems.  I think it was the cruft left over from the upgrade - related to a monster upstart/systemd system and mixed ifupdn and netplan junk.  At the time, netplan just wasn't ready for more complex needs, so I knew to wait and watch.  Took until 2021 before netplan supported the networking stuff I use on most of my servers, at least in a way I could get working.

> Touching a file seems to have solved the problem.
No, not solved. That is a gvfs problem.  Switch to autofs to manage the mounts and it will not happen again.  Also, please add a label. You'll thank me.  LABEL=XYZ can be used in any place that UUID=23432-2134223-42342332-42334223-234234-23423324632234-212234213-6523423423 can be used.  Mount, autofs, fstab. They all know how to use any links listed under /dev/disks/ ... to mount.

---

### Post by raleigh3 on 2022-09-30
```
No, not solved. That is a gvfs problem. Switch to autofs to manage the mounts and it will not happen again. Also, please add a label. You'll thank me. LABEL=XYZ can be used in any place that UUID=23432-2134223-42342332-42334223-234234-23423324632234-212234213-6523423423 can be used. Mount, autofs, fstab. They all know how to use any links listed under /dev/disks/ ... to mount. 

```
Could you give more details on autofs?

I am working with this.

I may need more help.

[https://linuxhint.com/mount-filesystems-automatically-on-demand-using-autofs/](https://linuxhint.com/mount-filesystems-automatically-on-demand-using-autofs/)

Thanks.

---

### Post by raleigh3 on 2022-09-30
I am stuck at this point. I have no /data directory.

```
The/data directory and the subdirectories fs1/, fs2/, and fs3/ should be automatically created, as you can see in the screenshot below.
$ ls /data

```
[https://imgur.com/a/8mvbROE](https://imgur.com/a/8mvbROE)

[https://linuxhint.com/mount-filesystems-automatically-on-demand-using-autofs/](https://linuxhint.com/mount-filesystems-automatically-on-demand-using-autofs/)

---

### Post by TheFu on 2022-10-01
[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs) seems reasonable.

There's only 1 trick ... if you call it that.
In the auto.master file, if the line for each mount group has a trailing '-' on the directory, then those mount points will be from the specific directory as said in the other file referenced. For example, 

```
/-    /etc/auto.misc --timeout=60 --ghost
/-    /etc/auto.nfs --timeout=60 --ghost
/Data /etc/auto.Data --timeout=60 --ghost
```

So, all the mounts in auto.misc and auto.nfs will be located in the directories those files contain directly.
However, all the mounts in auto.Data will be under /Data and that directory must pre-exist before autofs is started. It isn't created magically.

If you post your auto.master and relevant mount group files, it should be trivial to see issues.  No images. I don't click on external links with image from here. Sorry.

I use the "ghost" option so the directories for the mounts are shown, even when they aren't mounted.  This is handy for people using file managers, since without it, the directories don't exist and cannot be clicked on ... which causes the mount to happen ... any attempt to access any files under the mounted location will cause autofs to mount the specific file system.  The method used to access the storage doesn't matter.  GUI, CLI, cron, manual, doesn't matter.  'ls /path/to/some/file/under/the/mount' will cause it to mount just as easily.

I'm not really feeling the linuxhint example using sdb as a filename for settings.  Too easy for noobs to confuse that random filename with a device and device names aren't static.

---

### Post by raleigh3 on 2022-10-03
I have 20.04 on another partition. 

I am pretty certain most things still work on 20.04  that worked on 18.04.

I will "hang on" to 18.04 for a while longer. :-)

---

### Post by raleigh3 on 2022-10-05
I figured out the correct entry for fstab which solved the problem.

```
UUID=5b4b2ae5-9aaa-4559-9f41-afb313998c75    /media/andy/5b4b2ae5-9aaa-4559-9f41-afb313998c75    ext4    defaults 0   0
```

---

