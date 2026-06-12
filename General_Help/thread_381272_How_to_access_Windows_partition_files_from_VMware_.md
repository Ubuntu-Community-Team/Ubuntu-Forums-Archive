---
title: "How to access Windows partition files from VMware Workstation running Ubuntu as Guest"
date: 2007-03-10
forum: General Help
---

### Post by Ian Edmont on 2007-03-10
Hi,

Looking for some assistance please community. Recently started using VMware Workstation in Windows XP and am running Ubuntu 6.10 as Guest.

Can anyone please explain how I go about accessing files that are stored on my Windows partitions? I have Googled but not sure exactly what I should be querying!??!

Many thanks.

IE

---

### Post by Enki on 2007-03-10
In VMware, go to VM; settings; options; shared folders. Choose add, and select a folder on the host OS. In your VM, you will find your shared folder under /mnt/hgfs/

---

### Post by Ian Edmont on 2007-03-11
Thanks for the reply Enki. Will this mount be automatic?

Ian.

---

### Post by Enki on 2007-03-11
No problem. Yes, it should automatically mount. It does on my Xubuntu VM, even without restarting it.

---

