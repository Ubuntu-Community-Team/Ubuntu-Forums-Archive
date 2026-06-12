---
title: "Linux (Ubuntu) Back Plans"
date: 2017-08-22
forum: General Help
---

### Post by SpikeLS6 on 2017-08-22
CrashPlan for Home I have been using for Cloud backup is ceasing operations. Is there another Linux Ubuntu 17.4 compatible commercial back up plan or company out there that anyone uses or can recommend? 

If not and I buy a SSD for back ups, what automatic backup software will work best that anyone has experience with? I am not sure that Acronis will work with Linux.

Spike

---

### Post by TheFu on 2017-08-23
duplicity. [http://duplicity.nongnu.org/](http://duplicity.nongnu.org/) There is a package in the Ubuntu repos. Use the crontab to automate it. 

spideroak is a cloud backup option. [https://spideroak.com/faq/which-linux-distributions-and-releases-are-supported](https://spideroak.com/faq/which-linux-distributions-and-releases-are-supported) I've never used it.

Duplicity has built-in push support using all sorts of protocols, including S3.
[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto) is the how-to for Ubuntu.

BTW, I don't use duplicity for my backups.  I use rdiff-backup for a number of reasons, but if you want data stored in the cloud (which I would NEVER do), then encryption before it leaves your LAN is mandatory.

---

### Post by mastablasta on 2017-08-24
aside from Duplicity you might also expore Duplicati (a C# re-implementation of Duplicity) and if you don't mind Java also Areca is worth to be looked at. in Areca you can setup yoru backup witha nice GUI and then it iwll create a script from it which you then add to cron to automate it and so you do not have to run any GUIs.

if you encrypt the data well then it doesn't matter that much to what cloud you then back it up to (Google Drive, OneDrive, Dropbox...)

of course nothing beats having oyur own cloud or server (one can use the cheap Raspberi pi for that).

---

### Post by SpikeLS6 on 2017-08-24
Thank you for the replies. It appears rdiff-backup may work for me. I have a number of current hard drives replaced by SSD's in my PC available with plenty of space.

---

### Post by TheFu on 2017-08-24
If you go with rdiff-backup, best not push those files to the cloud without some extra encryption step.  That will make the differential pushes highly inefficient, because encrypted data appears like garbage from the outside.

To avoid viruses that deal with network storage, it is best to use a rdiff-backup "pull" from a different machine. That way, the storage used for backups isn't directly accessible FROM the machine to be backed up.  Lacking that, minimize the time that the backup storage is mounted to just to times DURING the backup processing.  There are a few ways to accomplish that - via direct mount/umount or autofs.  It would be bad if some CIFS/network storage virus destroyed all the backups, that's all.

The best how-to I know for rdiff-backup: [https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/)  - but that seems to be gone now. Use archive.org to get the original.

---

### Post by SpikeLS6 on 2017-08-26
I also found "udopp" and I may just do back ups to a USB stick. I realize it will not be in real time every 15 minutes or so, but I will just have to be more diligent with backing up. Bye Bye convenience. Thanks for the tips and information.

---

