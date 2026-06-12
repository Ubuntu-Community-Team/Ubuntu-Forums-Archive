---
title: "Error When Mounting a HDD"
date: 2016-10-05
forum: General Help
---

### Post by Incarnadine on 2016-10-05
I receive the following error when trying to mount a HDD:

> Unable to access “250 GB Volume”
Error mounting /dev/sdb1 at /media/emma/38B8F428B8F3E1F4: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/emma/38B8F428B8F3E1F4"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

Any ideas how to mount this HDD would be greatly appreciated!

---

### Post by QIII on 2016-10-05
Is this on a dual boot Linux/Windows machine?

Was the drive taken from a Windows machine and placed in a Linux machine?

The message indicates that the drive is in a Windows hibernation state.  Linux won't mount it because doing so might damage the NTFS file structure.

To be able to mount it, you will have to boot Windows, mount the drive and fully shut down Windows rather than entering the hybrid hibernation state Windows uses to make it appear your machine is booting quickly.

---

### Post by Incarnadine on 2016-11-15
> **QIII said:**
> Is this on a dual boot Linux/Windows machine?

Was the drive taken from a Windows machine and placed in a Linux machine?

The message indicates that the drive is in a Windows hibernation state.  Linux won't mount it because doing so might damage the NTFS file structure.

To be able to mount it, you will have to boot Windows, mount the drive and fully shut down Windows rather than entering the hybrid hibernation state Windows uses to make it appear your machine is booting quickly.

Thank you for pointing that out. I booted the HDD on a Windows machine and it worked.

This is why one shouldn't work in a zombie like state, you'll miss understand simple error messages like this :oops:

---

