---
title: "root group GID 998 and oot group GID 0?"
date: 2024-08-20
forum: General Help
---

### Post by myootnt on 2024-08-20
Hello,

I just downloaded 24.04 server image for Pi and copied it onto an external drive, booted, configured, all good. I wrote the image I used for that instance onto the Pi (CM4) local storage. I booted up, started to do things and I noted that directory perms were weird. By weird, I mean that the user was root and the group was oot on system directories. I checked in /etc/group and found this: oot:x:0: root:x:988: Both instances had nothing more than raspi-config installed with apt and updates.
A couple of google searches yielded nothing. The install on the external drive is normal, root:x:0: no "oot" 


<edit> I think I figured out part of what happened, I probably fat-fingered the r off root in the group file, the ID is persistent so things continued to work, but what is curious, is that something would go ahead and create a group with the root label if root were missing from the group file.

---

### Post by TheFu on 2024-08-20
There are very few mandated things in Unix-like systems, but
root uid = 0
and 
root gid = 0
are 2 of the mandated things. Period. No exceptions, unless you want to break a system.

Please use the Thread Tools button to mark this thread as "SOLVED", so others don't waste time on something that is solved.

---

