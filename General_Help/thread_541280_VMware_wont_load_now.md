---
title: "VMware wont load now"
date: 2007-09-02
forum: General Help
---

### Post by gargo2000 on 2007-09-02
I have VMware working for awhile now, but just today after a reboot, when I go to start VMware, it attempts to load then it just shuts down, I get no screen.  Only thing I get is in the taskbar "Starting VMware Server Console" and then it disappears.  

Any ideas to fix it?

Gargo

---

### Post by gargo2000 on 2007-09-02
Ok, some how the configuration changed for some reason, wondering if it was an update in ubuntu.  But went through the config of vmware and had to download the new kernals.  Now I am able to load VMware, but new problem....  Trying to open a previous installed Win XP and this is the new error:  "Cannot open the disk '/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmdk' or one of the snapshot disks it depends on.
Reason: Failed to lock the file."

Thanks for anyone's help in advance!

---

### Post by PilotJLR on 2007-09-02
Go into the folder with these VM files, and delete everything with a .LOCK or .LOCKED suffix.

Obviously, don't delete anything else  ;-)

---

### Post by gargo2000 on 2007-09-02
thanks for your reply.  I don't know what I did, but it did end up working on it's own...it was wierd.

---

