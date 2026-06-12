---
title: "Properly unmounting samba share on shutdown/reboot?"
date: 2019-03-24
forum: General Help
---

### Post by sapears on 2019-03-24
Hi all, i currently have a samba share on my network that i mount when my laptop is connected to the wifi, i mount it by a script in /etc/network/if-up.d/ which mounts it based on the line i added to /etc/fstab, which has the noauto option to stop it trying to mount the share on start up before the network is up

The issue i have is that when i disconnect from the wifi, the system hangs while it times out waiting for a response from the network drive, this lasts for 90 seconds.. If it happens when i'm logged in, the system only hangs if i use the df command or try to ls the mounted drive, or presumably any other command which would interact with the mounted drive. I got around this for the time being by adding a umount script in /etc/network/if-post-down.d/ which forces the drive to be unmounted with the -f flag..

The bigger problem is when i shutdown or reboot, the system takes ages to to stop while it does the same timeout thing, and regardless of any script in either if-post-down.d/ or if-down.d/ that should force umount the drive, it doesn't seem to trigger when i shutdown/reboot with the wifi still connected, like it does when i simply just manually d/c the wifi while being logged in..

Any ideas on how i'm actually meant to handle unmounting a network drive when i shutdown or reboot? Also any ideas on possibly a better solution to unmounting the drive when i d/c the wifi while logged in, other than using umount -f?

Thanks

---

### Post by TheFu on 2019-03-24
I use **autofs** for all temporary storage and networked storage.  It supports a "soft" mount option which handles missing access to storage much better than the default "hard" mounts.  Storage locations are only mounted when requested. After a few minutes of disuse, the mounts are released.  Autofs is a wrapper about the old automounter solution from the 1990s.  

Autofs is a client-side only setup.

---

