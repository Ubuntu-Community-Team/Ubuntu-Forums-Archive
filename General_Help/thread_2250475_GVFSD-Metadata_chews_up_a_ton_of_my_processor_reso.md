---
title: "GVFSD-Metadata chews up a ton of my processor resources"
date: 2014-10-28
forum: General Help
---

### Post by patagriff253 on 2014-10-28
GVFSD-Metadata chews up a ton of my processor resources. When I kill it with the task manager, my computer works great. What is it? Why do I need it? Can I kill it permanently? If so, how?

---

### Post by bapoumba on 2014-10-29
May be here : [http://ubuntuforums.org/showthread.php?t=1421580](http://ubuntuforums.org/showthread.php?t=1421580)

---

### Post by patagriff253 on 2014-10-29
Solution is no more permanent than using task manager to kill the process. I also have 75% free space on my hard drive, so I doubt this is the cause. It never happened until I upgraded to 14.04 LT.

I need a permanent fix.

---

### Post by patagriff253 on 2014-10-29
What if I changed the priority for this process?

---

### Post by bapoumba on 2014-10-29
I'm not sure there is a permanent fix : [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/517021](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/517021)

---

### Post by pvelkovski on 2014-12-29
This problem has been driving me crazy for the past few days on ubuntu 14.04. I have no idea what trigered this bug, but now, after using Ubuntu 14.04 for 2 months it started with this anoying behaviour.

Try this command:
sudo chmod -x /usr/lib/gvfs/gvfsd-metadata

It should disable gvfsd-metadata - the "-x" is making gvfsd-metadata non executable. Since i'm not sure of the side effects it might have on the system, if you want to reverse the command, just do:

sudo chmod +x /usr/lib/gvfs/gvfsd-metadata

---

### Post by pjpreilly on 2015-03-06
I can cause this at will by using Super Start in Firefox. When I right click & "Add this page to Super Start" on any page it  causes this gvfsd-metadata bug & is not related to Nautilus (Thunar  running). Linux Lite 2.2 (Xubuntu 14.04 w/ xfce 4.12). I notified Super Start support.

---

### Post by pjpreilly on 2015-03-06
Can anyone else confirm the ability to recreate this?

---

