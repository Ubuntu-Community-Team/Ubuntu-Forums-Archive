---
title: "fsck continually fails on boot - (unexpected inconstancy)"
date: 2012-11-28
forum: General Help
---

### Post by daulpavis on 2012-11-28
I continually get fsck failure messages on boot. I select option to fix where it claims to fix multiple orphaned nodes.
Within a reboot or so the message returns.


```

fsck from util-linux 2.20.1
rpcbind: Cannot open '/run/rpcbind/rpcbind.xdr' file for reading, errno2 (No such file or directory)
rpcbind: Cannot open '/run/rpcbind/portmap.xdr' file for reading, errno2 (No such file or directory)
/dev/sda5 contains a file system with errors, check forced.
/dev/sda5: Inodes thatwere part of a corrupt orphan linked list found.

/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
mountall: fsck [300] terminated with status 4
mountall Filesystem has errors: /
Checking disk drives for errors. This may take several minutes.
keys:Press C to cancel all checks in progress

keys:
Errors were found while checking the disk drive for /.
keys:Press F to attempt to fix the errors, I to Ignore, S to skip monting, or M for manual recovery

```

so sda5 is my root partition. I don't think the rpcbind errors are related, they existed before and I have read that they are common and to be ignored.

I recently upgraded from 12.04 to 12.10. I think the message started at this time, but can't be sure its related.

Running Ubuntu 12.10 on ASUS zenbook ux31 with SSD partitioned between Win7 and ubuntu. Win7 appears to be fine so I don't think the disk is failing. 

Any idea what this could be caused by and how to remedy the situation would be great

Thanks.

---

### Post by SeijiSensei on 2012-11-28
Reboot and select recovery mode from the grub menu.  Choose the root shell option when it is offered.

Now run this from the # prompt:

```

mount -o remount,rw -n /
fsck /dev/sda5

```

Say yes when prompted.  When it's done, reboot.  Note that there is no space in the parameter "remount,rw".

---

### Post by daulpavis on 2012-12-02
Thanks for the reply. No luck there though. It refused to run fsck after that re-mount.

I have been looking at the output of running fsck in manual recovery. It looks like the list of inodes which are fixed are almost identical each time.

I'm attaching photos showing the output from fsck from two consecutive failed boot attempts. The names show date stamps to give the order if that helps.

Does this help anyone out there identify what's going wrong?

Thans

Paul

---

