---
title: "[SOLVED] Mount Digital Camera/USB devices"
date: 2008-06-13
forum: General Help
---

### Post by Coppy on 2008-06-13
Hi,

After Ubuntu has updated to to 8.04 Hardy Heron, there is a new admin application to give app rights to users. 

since then ubuntu has not been unable to auto mount usb devices.

I can mount using sudo root in xterm which is okay for me. but for secondary users I have been unable to sussesfully give the correct permissions to allow auto mount via this new app 


any help would be appreciated

---

### Post by AndThenWhat on 2008-06-13
What did you try under System->Administration->Authorizations ?

There is a property that says "Directly Access Digital Cameras."

That seems to be exactly what you are looking for.

---

### Post by Coppy on 2008-06-13
yeah I added permissions, grant always for "Directly Access Digital Cameras" and " mount file system for removable drives". logged out and back in to allow new group polices. and still 

Cannot mount volume. 
You are not privileged to mount this volume.


command line works fine.
root@Riven:/home/coppy# sudo su
root@Riven:/home/coppy# mount -t auto /dev/sdb1 /media/External/

---

### Post by Coppy on 2008-06-27
I finally found the problem.
I had created an auto mount in fstab for my external hard drive, that was set to sdb1 the same that the Digital camera was trying to use.
after commenting that out, The camera would then auto mount okay, but still I had insufficient privileges to view files on the camera

started terminal
sudo su 
polkit-gnome-authorization 

granted access by root, to Directly Access Digital Cameras.
solved

---

