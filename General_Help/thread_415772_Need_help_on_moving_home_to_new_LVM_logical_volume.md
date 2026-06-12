---
title: "Need help on moving /home to new LVM logical volume"
date: 2007-04-20
forum: General Help
---

### Post by fable on 2007-04-20
I recently added a new hard drive as primary slave.  Since my Ubuntu platform uses LVM, I created a new logical volume using the free space from the new hard drive.

I want to move my entire /home folder from / (root) to the new logical volume.  Can someone tell me how to do it?

I was thinking of creating a new home folder in the new logical volume, copy the files from the existing /home folder,  mount the new home folder and then dismount the old home folder.

After I mount it, how do I tell the system that use the new home folder?  Do I use symbolic link?

How do I ensure that the new home folder will be mounted every time I boot?

---

