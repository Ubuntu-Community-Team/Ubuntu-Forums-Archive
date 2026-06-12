---
title: "SD Card reader not working - tried other solutions with no success"
date: 2017-08-26
forum: General Help
---

### Post by teamzippy on 2017-08-26
Here's the error that I'm getting: An error occurred while accessing '120.2 GiB Removable Media', the system responded: The requested operation has failed: Error mounting /dev/sdb1 at /media/spencer/64B0-8FF6: Command-line 'mount -t "exfat" -0 "uhelper=udisk2,nodev,nosuid,uid=1000,iocharset=utf8,namecase=0,errors=remount-ro,unmask=0077" "/dev/sdb1" "/media/spencer/64B0-8FF6" exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

Sorry for what I realize is one of many posts on SD cards. But I just am at the end of my rope. I've updated udisk2, I've tried the various instructions on mounting SD cards. Not sure what's left. It SEES it, as you can see, but it won't mount it. I should say I'm using an old 32 bit tower computer as a media server. So its a pretty old device.

Thanks for any help.

---

### Post by HermanAB on 2017-08-27
unknown filesystem type 'exfat':
Are you sure that the thing is exfat?  Since exfat is not installed on your system, so it never can mount that.

Run gparted or fdisk and see what it really is.

---

