---
title: "Mounting Issue Assist?"
date: 2014-02-16
forum: General Help
---

### Post by cathect2 on 2014-02-16
Hi, I have a drive partion that mounts as /backup. However, I can't get it to show up under "devices" in Nautilus or appear on my desktop. Below is my fstab file. What do I need to do to get this to auto-mount as a device? Thank you!

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=e952bc6e-1919-48c4-8585-8d375ca7e28c /               ext4    errors=remount-ro 0       1
# /backup was on /dev/sda1 during installation
UUID=ab8f0ed1-1f0d-4276-b47e-4946bd6412e9 /backup         ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
#UUID=b7a22ef0-397e-4c86-8a70-0784a06dc536 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

---

### Post by wiremoons on 2014-02-16
Hi cathect2

I dont know how to get the */backup* mount to appear under the 'Devices' section of the Nautilus window - but there is an easy alternative that might be ok for you to achieve something similar, and give you a short-cut link to the */backup *location. Try this:

1) Open the Nautilus file browser window
2) Browse so that you are located in the /backup mount (ie Click on '*Computer*' under the Devices heading - then double click the '*backup*' folder so you can see the files and/or directories located in your mount point)
3) On the top right hand side of the Nautilus window there a **cog wheel icon** - click it so the menu appears
4) From the menu choose the option:  "**Bookmark this location**"

This should add your mounted */backup* mount point location to the Nautilus as a Bookmark - located just beneath the 'Devices' section?

Hope that helps - or gives you a work around for now.

If you dont like the bookmark you just created - right click on it (ie its name under the "Bookmarks" heading) and choose "remove" from the popup menu.  You can add any folder/directory location to Nautilus using this method - so you have quick access to different locations on your file system.

---

### Post by deadflowr on 2014-02-16
Since you've added the mountpoint to fstab, it'll show up within the file system.
You've made the mountpoint /backup, so the question is, did you make a directory /backup?
The /backup will be listed as a separate directory from /home, like /usr, or /var, or /etc.

You can find it, if made, by selecting the option in nautilus' side panel, Computer(or if using 12.04 filesystem).

ninja'd, and +1 to using bookmarks for it.

---

