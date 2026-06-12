---
title: "http boot server"
date: 2022-07-29
forum: General Help
---

### Post by wcnackers on 2022-07-29
Hi,

Wasn't sure if this should be posted in networking or here so if it has be moved, I can move it.  Let me know.  Anyway...I have been tasked with setting up an HTTP boot server on Ubuntu.   The problem is (a) the only directions I have been able to find reference SLES and (b) the powers that be are not going to spring for a serer OS...has to be done, with the exception of my time, free.

Does anyone know if an HTTP boot server can be setup on the desktop version of Ubuntu and if possible if there is a tutorial or instructions available?

Thanks,

wcn

---

### Post by TheFu on 2022-07-29
Is this what you seek? [https://ubuntu.com/server/docs/install/netboot-amd64](https://ubuntu.com/server/docs/install/netboot-amd64)
Canonical has drastically changed netbooting between 18.04, 20.04 and 22.04. I think each uses a different method and some things never worked right at all.

I've only played with booting inside a VM just to see that it was possible. I used NFS, not http, for the task about a year ago with a 20.04 box. I don't have a spare physical machine laying around to do physical install testing, sorry.  My test was more about automatic installation into a VM than netbooting. I was mostly interested in setting up a disk layout with LVM and all the LVs I wanted.  And, I had ZERO interest in desktop installs, just servers.

I think these were the instructions I followed: [https://ubuntu.com/server/docs/install/autoinstall-quickstart](https://ubuntu.com/server/docs/install/autoinstall-quickstart)

I've never seen any method to netboot an Ubuntu Desktop.  In the old days, I think they used Cobbler for that, but I don't actually know.

Here's a VERY fast youtube video showing how to network boot Ubuntu desktops for 20.04 and 22.04:   [https://www.youtube.com/watch?v=Kb95YQYtexg](https://www.youtube.com/watch?v=Kb95YQYtexg)
To get everything, you'll likely need to pause every few seconds. He moves really fast!  He's using PXE boot from a tftp server.

---

