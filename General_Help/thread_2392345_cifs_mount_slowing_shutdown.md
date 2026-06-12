---
title: "cifs mount slowing shutdown"
date: 2018-05-20
forum: General Help
---

### Post by zachalexy on 2018-05-20
Hi, for months this worked great. Now, since a few days shutdown takes ages since Ubuntu (16.04) waits for unmounting my cifs share (automounted at boot). Is there an easy fix for this. My networking services (WiFi) seem to be gone before the unmount can take place (old issue) but has this come up again? Already done the symbolic link thing but still no luck. Can I add a simple line to pre-unmount my cifs shares before shutdown? Thx, Zach

---

### Post by TheFu on 2018-05-20
When things start behaving as you've described, I start by looking for hardware issues first. Check the logs. Look for disk errors, cable errors, connection problems, power issues.

Next, I look for any software changes that might have happened.  I'll get a list of the software versions and look for bugs, release notes, anything related to changes.

You lost me on the wifi and symlink comments. Please explain like we don't  know what you are talking about.

As for how to deal with remote CIFS mounts, there are 3 ways.
* fstab
* autofs
* manually, perhaps with a script.
I use autofs and manual scripts. I only use CIFS to connect to a Windows machine. For Unix-to-Unix connections, I use NFS (fstab/autofs).

Might be helpful to see how you mount it and a little knowledge about the CIFS server box?

---

### Post by zachalexy on 2018-05-20
Hi, I mount my SAMBA/cifs via fstab: //192.168.178.246/media /media/SAN cifs username=guest,password=,uid=1000,users,iocharset=utf8,noauto 0 0 and this works fine. Problem now occuring is that at shutdown/restart Ubuntu wants to unmount this share but (probably) my networking services are already down at this moment. What i've read on the net so far is that it is a common (older) issue but the typical solutions mentioned don't seem to solve my issue here. Maybe I should search the solution in terms of a script (with the umount command) that runs just before shutting down (via dispatcher/...?). If I manually unmount before rebooting Ubuntu flies to reboot. Otherwise it keeps waiting and waiting to release the cifs share mentioned above. Don't know much about cifs/server; mainly standard Ubuntu i would say.
Thanks again, regards, Zach

---

### Post by zachalexy on 2018-05-20
Hi, found it. Added a script in the pre-down.d subfolder (/etc/NetworkManager/dispatcher.d/pre-down.d/) with the umount command. Restarting is fun again ;-). Thanks for your help.

---

### Post by Morbius1 on 2018-05-20
What was the script? This sort of thing can help many users.

Was it just a **umount /media/SAN**

---

