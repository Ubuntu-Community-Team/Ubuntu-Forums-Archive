---
title: "Image based cloud backup?"
date: 2014-09-12
forum: General Help
---

### Post by dorlow on 2014-09-12
I have an interesting question.  I have my Ubuntu Linux running about perfect.  I was wondering if there was such a program that would constantly backup my PC in the background.  But I want it to be imaged based.  So, if my PC for whatever crashed, I could load Ubuntu again or maybe have a boot disk, then it would go out to the cloud and pull down an exact image of the last time it was working right and reinstall programs, put my files back, put custom scripts I have all over my hard drive back in, etc...  Right now I'm using Crashplan.  It works.  But if my PC's hard drive dies, I have to reinstall Ubuntu, then reinstall all my apps and try to get them working right.  Find licenses to get everything registered again.  But I can download all my files from Crashplan.  But it won't setup my PC the way it was before.

---

### Post by rbmorse on 2014-09-12
Unless you're running an LVM disk subsystem, Linux does not support "live" imaging of mounted disk partitions.  Even with LVM disks, imaging mounted partitions is a bit involved.  The closest I've been able to come is to shut down the entire Linux session, boot into an alternative environment and create the disk images and copy/move them to the storage medium from there. The storage medium in this case being a trio of WD 1TB Passport USB3 portable drives that are rotated off-site to provide some protection against loss of the local machine to theft or mishap, or if Godzilla steps on the house or something like that. 

In my case, I'm using the Macrium Reflect bootable recovery Flash drive to create the partition images (I had a license left over when I abandoned Windows) but there are plenty of useful Linux-based tools that will do the job, too.  Just not automatically and in background, or without having to boot into another operating environment.  

The ability to restore a partition from an image is well worth having.  Using the leftover Macrium Reflect I can restore the /root drive and/or the /home partition (separate physical drive) in about 5 minutes each.  Reinstalling Ubuntu from scratch takes at least an hour and usually more,  even if I am able to restore the /home and /etc partitions from file-based backups. 

As you can tell, this whole scheme depends upon me stopping whatever I am doing with the machine to create the backup image(s) and that's the weak point.  If I don't have the right round tuit, the backup doesn't get done on schedule, and if there's no predictable schedule for the backups then there really isn't any backup. It's just have a collection of old files.  I try to refresh the saved images at least once a week. 

To supplement the image effort, and partially ameliorate it's shortfall, I also use the "BackinTime" utility from repository to create an automatic file-by-file copy of / and all it's subdirectories once a day. This file set is stored on a dedicated drive that is a different physical drive unit than the ones holding / and /home.  It won't put the machine "back to the way it was" like the backup image of a partition will, but it does make sure that the safety copy of every file on the machine gets refreshed at least once a day.  "Back in Time" does a good job of managing the data store...right now I have it set to retain just the last seven dailies, but it can easily be configured to automatically run any data archiving schedule one might need.

On the last part, mirroring to a cloud storage,  If you use Google drive (cheap, but not as cheap as it used to be) and the Chrome browser, Google has an "app" called "Insync" that will mirror any selected file or directory on your local machine to your on-line Google drive (and vice-versa, but check the size of the data store before you implement the last part).  These are file copies, not partition images. Changes are made almost real-time so if you delete a file on the local machine it's gone from the Google Drive, too.  That doesn't happen immediately, though, files deleted from Google Drive via Insync go to a trash can from which they can be recovered, if you get there soon enough.   I don't know how long files last in the trash can...there may not be a set schedule.  Insync really benefits from a fast Internet connection, although once the initial sync takes place (can take days depending upon the size of the data set) my installation doesn't have any problem keeping up on a 20/5 Mbps cable connection.   I have the wife's MacBook on a similar scheme with an Apple time machine and it does fine over an 802.11ac wireless link (after the initial store is set up and sync'd, of course).

---

