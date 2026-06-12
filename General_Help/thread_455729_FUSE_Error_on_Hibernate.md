---
title: "FUSE Error on Hibernate"
date: 2007-05-26
forum: General Help
---

### Post by DocHoliday52090 on 2007-05-26
I'm getting a strange error when hibernating. 

> /usr/sbin/hibernate: 869: /usr/local/sbin/network-manager-ctrl: not found
/usr/sbin/hibernate: 869: /usr/local/sbin/network-manager-ctrl: not found
hibernate: Aborting suspend due to errors in MiscLaunchAuxFunc2 (use --force to override).
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/disk/by-uuid/A4C82B3EC82B0DDC ()


Feisty Fawn/Compaq nc6220
Suspend2 Patched
3 SMB network drives automounted on startup
1 NTFS Local

I was having swap issues before (it wasn't loading on startup), so I changed the UUID to a simple /dev/hda5, which seems to work. 

Any Solutions?

---

### Post by mbradlcu on 2007-05-27
Hi Doc,
sorry this isn't an answer but I posted a while back about having a problem with sshfs and the swap file. Basically after I came back to my machine left on overnight the mem usage was very high and the swap file was being accessed constantly. I had to umount all the sshfs mounts and do a swapoff-on to get my machine back to normal performance,, is that the same issue you were having?

---

### Post by DocHoliday52090 on 2007-05-30
Nope. 

It seems that /dev/hda7 (i think) refuses to unmount correctly

Because of that, it wont hibernate.

I can go through this through "sudo hibernate -f", but it won' t resume - it just boots up again like a normal boot.

---

