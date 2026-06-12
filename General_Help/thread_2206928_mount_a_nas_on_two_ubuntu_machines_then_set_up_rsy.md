---
title: "mount a nas on two ubuntu machines then set up rsync to back up to different shares"
date: 2014-02-21
forum: General Help
---

### Post by sgurski on 2014-02-21
I'm trying to find out if this is going to be a problem before I do anything. I can't afford another mistake right now. I currently have my nas drive mounted to a virtual machine. I already have a cron job set up to back up data from there to the nas in a specified folder. what I would like to do is mount the same nas on another computer, create a cron job to back up a virtual machine in another folder on the nas. Would this in any way cause problems with either backup? would there be any sort of conflict if the two jobs crossed over time wise? Do I have to have the VM shut down to run rsync on the image? I imagine this may be a lot to answer but any help and guidance would be greatly appreciated!

---

### Post by TheFu on 2014-02-21
Welcome to the forums.

It depends on the NAS and the implementation of the protocol used.
If they implement CIFS or NFS correctly, and your backups are written to different file areas, then there shouldn't be any issue besides slower performance due to network and disk IO contention.

I wouldn't be worried at all.

---

