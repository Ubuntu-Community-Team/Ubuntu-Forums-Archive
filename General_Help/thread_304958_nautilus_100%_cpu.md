---
title: "nautilus 100% cpu"
date: 2006-11-22
forum: General Help
---

### Post by dguido on 2006-11-22
I keep a system monitor in my gnome taskbar and routinely (about once a day), I see it spike up to 100% and stay there while I'm doing nothing but browse the internet.  If I open up a process list, I see that the culprit is always nautilus.  If I kill nautilus, it automatically restarts and its CPU use goes down to what it should be (1-2%).

Does anyone know how to debug this strange behavior and find out what's causing it?  I'm not sure but it might be related to having preview windows of movies and images open, but I can't be sure.

---

### Post by ebash on 2006-11-22
There's a bug with nautilus under edgy that produces a similar behavior. If there's a nautilus window open on a folder that has a file that's been uploaded nautilus will start using 100% of CPU.

If you have nautilus open in the folder where you download files then you will be experiencing that very same bug.

---

### Post by Azathoth_ on 2006-11-22
I think it has been solved... find the issue in launchpad... i installed libgnomevfs2-0-dbg_2.16.1-0ubuntu3_i386.deb, libgnomevfs2-bin_2.16.1-0ubuntu3_i386.deb, libgnomevfs2-common_2.16.1-0ubuntu3_all.deb, libgnomevfs2-dev_2.16.1-0ubuntu3_i386.deb and
libgnomevfs2-extra_2.16.1-0ubuntu3_i386.deb and i think it has been solved... anyway search for this issue in launchpad

---

### Post by dguido on 2006-11-22
[https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684](https://launchpad.net/distros/ubuntu/+source/nautilus/+bug/54684)

Thanks.

---

