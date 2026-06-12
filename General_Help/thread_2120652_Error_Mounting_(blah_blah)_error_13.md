---
title: "Error Mounting: (blah blah) error 13"
date: 2013-02-27
forum: General Help
---

### Post by Nixarter on 2013-02-27
ok, Windows reads it fine and works with it like nothing is wrong.  However, if I plug the drive into a *nix box, i get an error and it refuses to mount even as read-only.  Here is what my Ubuntu says:

```
Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 3).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

What I have tried: remounting it in wondows, doing a "remove hardware safely" and then mounting in ubuntu.  This has no effect.

It is a new drive (just a month or two) and there is also plenty of free space on the drive, about 50%.  So there aren't any defrag or hardware issues.

How do I fix it?

And no, before you suggest it, chkdsk has no purpose other than corrupting perfectly good file systems and randomly deleting perfectly good data.  I refuse to run it on there.  If you think it is a decent option, leave this thread.  you are not welcome to post here.

---

### Post by dino99 on 2013-02-27
on which ubuntu is that happening ?
recently raring has got ntfs-3g updates/fixes (and cant say if they have been backported) and that was concerning the mount process.

[https://launchpad.net/ubuntu/+source/ntfs-3g](https://launchpad.net/ubuntu/+source/ntfs-3g)

is your /etc/fstab a genuine file ?

---

