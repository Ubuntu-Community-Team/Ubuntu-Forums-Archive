---
title: "portable hard drive keeps unmounting"
date: 2015-02-26
forum: General Help
---

### Post by Evil Wayz on 2015-02-26
I have one of those small form factor 2 tb passport hard drives.  It was working fine, but recently when it got close to full, it will unmount itself, and if I'm lucky it will remount a few minutes later.  If I'm not lucky I have to unplug it and then plug it back in.  I've tried error checking it with gparted and the check fails.  A similiar check with windows works, but it cointinues this pattern of mounting/unmounting.

---

### Post by TheFu on 2015-02-26
Sounds like the USB connectors aren't connecting very solid. Try different ports, different cables to make it go away.  Of course, I'd make a backup of the HDD, just in-case it is something more serious.

What file system is being used?  The native OS for that file system should be used to check it.

---

### Post by Evil Wayz on 2015-02-27
The cable isnt a standard big usb on one side/mini usb on the other its proprietary, not sure if I could order a new one or not.  The native file system is ntfs.

---

### Post by TheFu on 2015-02-27
> **Evil Wayz said:**
> The cable isnt a standard big usb on one side/mini usb on the other its proprietary, not sure if I could order a new one or not.  The native file system is ntfs.

That won't make solving the easier.  Could it be USB3 - which has different connection on the non-PC side.
Regardless, is there a way you can stabilize the cable connection against vibration?

Don't forget - use Windows to check the NTFS file system, not Linux.  Also, always "eject" the media before disconnecting it. On Linux, that's "umount".

---

### Post by tgalati4 on 2015-02-27
If the drive is near full, it has to work harder to find space to store stuff.  It's possible that you don't have enough power to run the drive in this condition.  Make some free space.  Quick.

---

### Post by Evil Wayz on 2015-02-28
> **tgalati4 said:**
> If the drive is near full, it has to work harder to find space to store stuff.  It's possible that you don't have enough power to run the drive in this condition.  Make some free space.  Quick.


Well that's just craptastic.  Thanks for the warning.

---

