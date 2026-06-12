---
title: "Ubuntu Server 17.04 Installed WEIRD!"
date: 2018-01-01
forum: General Help
---

### Post by XBMC old School on 2018-01-01
For S&G I installed ubuntu server to take  advantage of the Raid 0 Option (2-SSDs). I installed gnome via the  tasksel command and the PPA method and get the same result
 There are a whole “host” of issues; I can’t see my wired ethernet  connections (unmanaged), and I can’t run firefox unless it is as root,  thumbnails don’t show, etc.
 Did I miss something with the install? Does anyone gnow a solution.  Do i need to switch distribtutions to get a Raid-0 option on the  desktop?

---

### Post by TheFu on 2018-01-01
During install - choose "do something else" for the storage options.  From there, you can manually configure anything.  However, the Ubuntu storage setup during install is not nearly as good as for many other distros.

You could use LVM and have it create spliced RAID0, instead of trying to use mdadm.  Just an observation.

Server distros don't have as many "desktop" drivers included.  I always start with an Ubuntu Server install and usually don't have drivers for my NIC or wifi, though they are both available during the install.  

As for running GUI programs as root.  Don't.  Just don't.  Nothing good comes from that and it is easy for someone who isn't solid on their file and directory permissions to get their system into a state where they cannot login at all.

For most people, if you want a GUI, then install a desktop release.

BTW, support for 17.04 ends in 1-2 weeks, so trying to fix anything here is a waste of your time. In a few more weeks, nobody will respond to 17.04 posts.

---

