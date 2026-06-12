---
title: "Problem using USB device with NIS users but not with local users"
date: 2005-10-12
forum: General Help
---

### Post by rangzen on 2005-10-12
Hello,
i have a strange thing ...
When i plug a USB device like Iomega zip or USB key,
if the user is a NIS user, nothing happens, with a dmesg i can see that the device is know but nothing is mounted,
if the user is local, everything go fine, the device appears on the desktop

A precision, the $HOME of the NIS users is mounted by NFS

Any ideas ?

---

### Post by Alexander Kirillov on 2005-10-12
[QUOTE=rangzen]Hello,
i have a strange thing ...
When i plug a USB device like Iomega zip or USB key,
if the user is a NIS user, nothing happens, with a dmesg i can see that the device is know but nothing is mounted,
if the user is local, everything go fine, the device appears on the desktop

A precision, the $HOME of the NIS users is mounted by NFS

Any ideas ?[/QUOTE]
In order to be able to use automounting of plugged in devices, the user must be in the groups plugdev group. NIS users are not in that group by default. There was a discussion of this problem (and similar problems - like NIS users not able to access CD-ROMS or use sound) in many threads (search forums), like these ones:
[http://ubuntuforums.org/showthread.php?t=31542](http://ubuntuforums.org/showthread.php?t=31542)
[http://ubuntuforums.org/showthread.php?t=16035](http://ubuntuforums.org/showthread.php?t=16035)

---

### Post by rangzen on 2005-10-12
Thank you very much for your links !

---

