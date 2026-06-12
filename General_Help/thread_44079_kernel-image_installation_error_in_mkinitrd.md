---
title: "kernel-image installation error in mkinitrd"
date: 2005-06-24
forum: General Help
---

### Post by nictuku on 2005-06-24
Hi.

I have a software RAID-1 configured as the root file system of a server.

Whenever I try to install/update a kernel, I get the same error.

I believe it can be related to Debian's bug #266591, although that specific issue was fixed. It seems mkinitrd is wrong while gessing I#266591 have some LVM volumes, which I don't.

Thank you for any help.

This is the same error reported in another thread, but this is clearly not a 64bit architecture issue.

[http://ubuntuforums.org/archive/index.php/t-39838.html](http://ubuntuforums.org/archive/index.php/t-39838.html)
```


# apt-get install linux-image-2.6.11-1-686-smp
Reading package lists... Done
Building dependency tree... Done
linux-image-2.6.11-1-686-smp is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.11-1-686-smp (2.6.11-0.2) ...
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
File descriptor 7 left open
    Finding all volume groups
  No volume groups found
/usr/sbin/mkinitrd: /dev/evms/.nodes/sda5: Cannot find LVM device
Failed to create initrd image.
dpkg: error processing linux-image-2.6.11-1-686-smp (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.11-1-686-smp
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by skoal on 2005-06-24
I really don't have a clue what's causing it, but since you say you don't have any LVM devices, maybe backup /usr/sbin/mkinitrd, open it in an editor and comment/delete out any mention/call (invocation) of the function "lvm()" and try to install your kernel again.  Maybe that's a quick fix.

\\//_

---

### Post by nictuku on 2005-06-24
Ok, now that's a quick and dirty solution I haven't think about.

I've did it, and it installed.

Let me now reboot the server..ok. It didn't work.

debian-installer created the /dev/md1 RAID using /dev/evms/.nodes/(sda5|sb5), but mkinitrd couldn't manage that.

I wonder why debian-installer used that device instead of /dev/sd[ab]5.

In the end, I deleted the RAID as it was a bogus RAID for swap partitions, and created two swap from that.

Then it worked.

Now, something has to be fixed. Either the installer shouldn't have created the raid using those dev files or mkinitrd should understand those, even if the filesystem type is swap (this could be triggering the issue, too).

Am I wrong?

---

### Post by Ab3 on 2005-07-01
was getting the same error on a raid 1 config. deleted the /etc/mdadm/mdadm.conf file (after verifying that raid was ok) to get rid of the error.

---

