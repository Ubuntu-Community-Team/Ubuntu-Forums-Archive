---
title: "/user/share/mime/mime.cache"
date: 2015-08-22
forum: General Help
---

### Post by aziz07 on 2015-08-22
Hi,

I have deleted mime.cache in Lubuntu and Ubuntu 15.04 64bit as it was detected by Clam Antivirus. Under Lubuntu, deleting the mime.cache file does not affect system stability but it will reappear after several reboots, not after a single reboot. In Ubuntu, deleting the mime.cache file resulted in the desktop not loading. My question is since both OS are the same, why would it not affect Lubuntu? 
The system can run without the mime.cache file under Lubuntu. What is the detailed function of this file found in /user/share/mime/?

I opened the file with nano and here is what I found that is readable where it points out to the iptables directory:

Project-Id-Version:#.download.the.free.Google.Video.Player^@# download the free Google Video Player^@BEGIN:IMELODY^@^@^@/etc/sysconfig/iptables

Thanks

---

### Post by Dennis N on 2015-08-22
Another case here:
[http://ubuntuforums.org/showthread.php?t=2274088](http://ubuntuforums.org/showthread.php?t=2274088)
Post #3 explains **mime.cache**

---

### Post by aziz07 on 2015-08-22
Thanks for the reply, I have already read that and another thread about mime.cache. I think that some people have it clean because they have not selected the option to scan for PUA (Poetentially Unsafe Applications).
Still, why would deleting it not affect Lubuntu? Even after two or three reboots, ClamAV detects nothing in it until several reboots. Ubuntu won't even load desktop. Lubuntu can function well without it.

Perhaps, since its a cache file, can it be a program and/or a website causing this issue? How can I analyse this file other than using nano editor? 

Thanks

---

