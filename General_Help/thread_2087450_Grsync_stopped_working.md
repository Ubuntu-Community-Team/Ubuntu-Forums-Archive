---
title: "Grsync stopped working"
date: 2012-11-23
forum: General Help
---

### Post by John_Rose1 on 2012-11-23
Help, I am not a technical specialist.

I am running Ubuntu 10.04 LTS Lucid Lynx. I have been using rsync through Grsync for at least two years with this version to backup onto an external drive. Sometime in the last couple of weeks Grsync stopped working giving the following message:

*** Lancement de la commande RSYNC :
rsync -r -t -v --progress --size-only /media/OS/Pictures/ /media/LaCie/Back-up/images/

sending incremental file list
rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
rsync: ERROR: cannot stat destination "/media/LaCie/Back-up/images/": Permission denied (13)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(573) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]

The external drive is mounted and works fine from the desktop for copying and deleting files and folders. The only thing I can think of is that the Linux kernal was updated since the last time Grsync worked, it is now 2.6.32-45-generic .

Best regards, John

---

### Post by papibe on 2012-11-23
Hi John_Rose1.

Are both ext4 filesystems? 

At first impression, it looks like the typical problem of trying to create linux filenames into an NTFS filesystem.

Regards.

---

### Post by John_Rose1 on 2012-11-24
Hi papibe,

Some of the files that I am backing up in ext3 partitions and some are in NTFS partitions (different Grsync command for each folder being backed up). The receiving external disk has a single NTFS partition and is connected to my Dell portable through the eSata port. I have two back-up commands for ext3 to NTFS and two for NTFS to NTFS and all now fail the same way.

As I said my back-ups had been working perfectly since I installed Ubuntu 10.4 two years ago. If it is not something with the new Linux kernal (or some other recent Ubuntu package update), I have one other bit of information which could possibly (but I really doubt it) be useful: just a few days ago (perhaps before the Grsync failed) I used the external drive under my dual booted Windows XP, but I didn't write anything into the folders that receive my back-ups from Ubuntu. In the past use of the external disk under Windows had no effect on the operability of Grsync under Ubuntu.

Hope this helps to resolve, thanks so much, John

---

### Post by papibe on 2012-11-24
Could you post the results of these commands?
```
mount -l

df -h

id

ls -ld /media/LaCie/Back-up/images/
```
Regards.

---

### Post by John_Rose1 on 2012-11-25
Dear papibe,

I have attached the results as Grsync problem.txt . Seems that there may be some problems accessing the external disk but in the GNOME desktop I have no problem in creating or deleting folders and files on it, or in coping files to or from it.

Looking forward to your thoughts, thanks, John

---

### Post by papibe on 2012-11-25
Thanks.

It's a little late for me, but after a simple look it seems that the destination folder is owned by root, and your regular user does not have privileges to 'cd' or write on it.

Note that there's another directory called 'LaCie_' (not 'LaCie') that is owned by your regular user, so you should have all access there.

I'll take another tomorrow.

Regards.

---

### Post by John_Rose1 on 2012-11-25
Yes papibe, I noticed this too. When I change LaCie to LaCie_ in the Grsync commands, it works fine like before.

But I did not create LaCie_ , it was not there a couple of weeks ago and my files were at that time in LaCie. Windows could not have changed it since it is in the Ubuntu ext3 file system, so Ubuntu or one of its components must have done it.

Can you explain? Can I delete the system folder LaCie and rename LaCie_ to LaCie to get back to where it was before?

Thanks and best regards, John

---

