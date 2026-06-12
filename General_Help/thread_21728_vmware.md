---
title: "vmware"
date: 2005-03-23
forum: General Help
---

### Post by core on 2005-03-23
Hi. First post here. Should know i'm preety noob at this, installed hoary preview 2 days ago.

Question is, I have two disks, master with hoary, slave with windows xp. I heard about something called VMware that allows the user to bootup, in a separate window, from another disk or partition.

Now, although i've uncommented the hoary universe lines at etc/apt/sources.list, i can't find vmware there. Why is that? Is it because it's not free? How can I get vmware installed and running on my hoary? If it's not free then, is there any other similar and free software around?

Thanks in advance for any help.

---

### Post by ManiacMac on 2005-03-23
[www.vmware.com](www.vmware.com) is what you want to get going.  The application has a heafty price tag on it, but for people like myself (securty consultant and software developer) I find it invaluable.

Also, something you may want to look into is a hack for VMWare to allow for sound through ESD (as be default it talks directly to the device...bad).  You can get at : [http://knihovny.cvut.cz/ftp/pub/vmware/vmwaredsp-1.2.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmwaredsp-1.2.tar.gz)

NOTE: VMWare will NOT properly run an already installed Windows partition, because thanks to WinNT (NT, 2k, XP, 2k3) kernels, if the hardware is too different, the kernel will freak and bluescreen.

---

