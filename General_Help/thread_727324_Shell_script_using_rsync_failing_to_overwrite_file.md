---
title: "Shell script using rsync failing to overwrite files"
date: 2008-03-17
forum: General Help
---

### Post by roadkill on 2008-03-17
I've written a shell script which compares the timestamps on files stored on my PC and a flash drive, and copies the newest files from one location to the other and vice versa.  This is the script:

```
#!/bin/sh
#
# Script to copy newer files from flash drive to PC document folder and vice versa
#
# Check to see if flash drive plugged in
if [ -e "/media/disk" ]
then
# Copy newer files
rsync -avub --exclude '*~' /media/disk/*.html /home/chris/Desktop/shtest
rsync -avub --exclude '*~' /home/chris/Desktop/shtest /media/disk
else
echo "Test failed"
fi
```

When I run it, I get this output in the terminal window:

```
building file list ... done

sent 67 bytes  received 20 bytes  174.00 bytes/sec
total size is 0  speedup is 0.00
building file list ... done
shtest/
rsync: chgrp "/media/disk/shtest" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/shtest/test.sh" failed: Operation not permitted (1)
rsync: chgrp "/media/disk/shtest/testsync.sh" failed: Operation not permitted (1)

sent 179 bytes  received 38 bytes  434.00 bytes/sec
total size is 601  speedup is 2.77
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]
```

I'm not sure why the script is attempting to change the group, since I'm using the -a option (unless it's because the files on the flash drive I'm using to test the script were created on Windows?)  And what I've found after execution is that new files are copied across, but existing files aren't overwritten by newer versions.  It makes no difference if I sudo the script or not.

---

