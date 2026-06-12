---
title: "Bionic does not see USB hard drives"
date: 2018-12-07
forum: General Help
---

### Post by cscj01 on 2018-12-07
My Ubuntu 18.04 (Bionic) recently stopped seeing my external USB hard drives.  This is a serious problem because I use them for back up.  I ran ```
sudo fdisk -lu
``` and noticed I had nine /dev/loopn (n = 0 to 8).  I am not sure why I have these, but some posts on the Internet related them to Snap.  While I do not know if Snap is causing problems, I know I did not have /dev/loop devices when my USB hard drives were seen by the OS.  I am currently at kernel 4.15.0-42-generic (x86_64) and running Gnome Flashback.  I saw where someone suggested removing snapd and libsnapd-glib1, but that indicated that some programs/applications would be removed that I did not want to remove.  Does anyone have any advice of how I might find out why I cannot see my external USB hard drives?

---

### Post by cscj01 on 2018-12-08
I uninstalled snapd, and then I removed power to my external USB hard drives and applied power after a short period.  The system mounted them.  Any explanation for this behavior?

---

### Post by cscj01 on 2018-12-08
bump

---

### Post by oldfred on 2018-12-08
I have seen where unplugging a device and then replugging it back in, then does not show.
Somehow rebooting resets everything so it does show.
Other times device has shown up, but changed device to next letter, or from sdf to sdg for example.

Are you auto mounting with nautilus, manually mounting or using fstab?

---

### Post by cscj01 on 2018-12-08
> **oldfred said:**
> I have seen where unplugging a device and then replugging it back in, then does not show.
Somehow rebooting resets everything so it does show.
Other times device has shown up, but changed device to next letter, or from sdf to sdg for example.

Are you auto mounting with nautilus, manually mounting or using fstab?

I use fstab for my internal hard drives and nfs shares, but I let nautilus mount my external usb hard drives.  Perhaps I should change my external hard drives to fstab?

---

### Post by oldfred on 2018-12-08
I do not use fstab for any drive I unplug, but if always plugged in you may need mount parameters.
I have this in my notes, but often used with nfs mounts.
       use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections 
[https://www.linux.com/blog/how-configure-autofs-automount-linux](https://www.linux.com/blog/how-configure-autofs-automount-linux)

My backup to each flash drive is only when I plug it in & it has its own script to mount it as each has different labels. I try to mount by label now, so I know what the mount is. UUID does not tell me much.

---

