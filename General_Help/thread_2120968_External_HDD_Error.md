---
title: "External HDD Error"
date: 2013-02-28
forum: General Help
---

### Post by wrichtmyer on 2013-02-28
Hello!

My Windows bootloader died, and thought it'd be a good opportunity to come back to the Ubuntu community.

Unfortunately, when I tried backing up my information onto an external hard drive (an old Macintosh laptop drive, formatted in Mac OS Extended Journaled[HFS+]), the permissions for the external are set to read-only, and I'm not trying to format it. I tried resetting this under "properties", but I'm not the owner of the drive. I researched online, and I tried ```
gsudo nautilus
``` in order to get the proper permissions, but this didn't work either.

I tried fixing the drive by doing ```
fsck -r /dev/sdc2
```, but I got the error 
```
fsck: fsck.hfsplus: not found
fsck: error 2 while executing fsck.hfsplus for /dev/sdc2

```

Lastly, I tried ```
sudo apt-get install pysdm
```, but I believe this program's out of date, so I was 'unable to locate the package'.

I'm running Ubuntu 12.04 which is slightly out of date, but it is much more modern than the version I used years ago (10.04) or the forum posts are out of date. 

I'd be amazed if you guys could help me, let's see what happens! :popcorn:

---

### Post by fdrake on 2013-02-28
1. to fix an windows MBR you need a windows install cd, after you do that you need to update grub too.
2. Mac OS Extended Journaled[HFS+] > is the journal activated(is the journal NOT empty)? if yes then permissions cannot me changed.

if not then try:
check post #4 [http://forum.xbmc.org/showthread.php?tid=51626](http://forum.xbmc.org/showthread.php?tid=51626)

---

### Post by ajgreeny on 2013-02-28
You will need to make sure you have the package **hfsplus** installed on your ubuntu OS to be able to fully use and write to a partition formatted to hfs+.

---

### Post by tgalati4 on 2013-02-28
Although this was a few years ago, the hfsplus utiliities required turning off the journaling before being able to write to the disk.  I don't know if this is still a requirement.  This can be done on a Mac computer using "Disk Utilities" and turning off journaling in "Properties" for the volume (partition) that needs linux-write capability.

tgalati4@Mint14-Extensa ~ $ apt-cache search hfsplus
hfsplus - Tools to access HFS+ formatted volumes
libhfsp-dev - Library to access HFS+ formatted volumes
libhfsp0 - Shared library to access HFS+ formatted volumes
dmg2img - Tool for converting compress dmg files to hfsplus images

---

