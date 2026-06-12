---
title: "Possible to use variables in udev rule actions?"
date: 2013-05-25
forum: General Help
---

### Post by latestversion on 2013-05-25
I've set the following in a udev script to automatically mount/umount a BlackBerry when plugged into the laptop. However, I'd like to make the mount point of /media/blackberry a variable rather than specifying it 4 different times here. I'd like not to use another script, meaning in the 'RUN+=' rule not having to refer to a custom script where I place these rules. I tried using 'mkdir /media/$ID_MODEL', where ID_MODEL was set in the first line here, but that didn't work. Any way to get variables to work here?

```
ATTR{idVendor}=="0fca", ATTRS{interface}=="RIM Mass Storage Device", ENV{ID_MODEL}="BlackBerry"
ENV{ID_MODEL}=="BlackBerry", ACTION=="add", RUN+="/usr/bin/sudo /bin/bash -c 'mkdir /media/blackberry ; mount /dev/%k /media/blackberry'"
ENV{ID_MODEL}=="BlackBerry", ACTION=="remove", RUN+="/usr/bin/sudo /bin/bash -c 'umount /media/blackberry ; rmdir /media/blackberry'"
```

I thought specifying ENV{ID_MODEL} would mean that ID_MODEL would be  passed to the environment, but in the RUN+= section if I do a 'printenv  > /path/to/file' and inspect /path/to/file, it doesn't have ID_MODEL  there.

---

### Post by Rebelli0us on 2013-05-26
I have[ udev rule with a variable]("http://ubuntuforums.org/showthread.php?t=2120763&p=12562008#post12562008") that works ok

---

