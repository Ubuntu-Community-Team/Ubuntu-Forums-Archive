---
title: "About backup with sbackup ( simple backup )"
date: 2008-05-27
forum: General Help
---

### Post by sofasurfer on 2008-05-27
When using sbackup, is the full backup (done periodically) a disk image which can restore a wiped disk to create a bootable system or is it just a full file backup?

Is the section where you choose files to include just used for the incremental backup and thus, the full backup is by default always a full backup of "/"?

As to the directories that you exclude (for example, tmp, sys, proc, etc), when you restore the system do you need to recreate these directories or is this done by default?

I see in the tutorials about backing up with "tar" that it is nessessary to edit fstab and some other file to change the uuid and /sda* lines. Do I need to be concerned about this with sbackup?

Thanks for you help.

---

### Post by indytim on 2008-05-27
> 
When using sbackup, is the full backup (done periodically) a disk image which can restore a wiped disk to create a bootable system or is it just a full file backup?


I can't speak to sbackup, but if you are looking at a disk image backup, I'd suggest partimage (it's in the repositories).  I use it on a weekly basis to backup all of my resident Lx Ops and the associated /home partitions.

IndyTim

---

### Post by Hozza on 2008-05-27
I installed sbackup about 20mins ago and from what I gather it is a full file backup not a disk image backup. (I could be wrong)

It will only back up the folders that it says it will and when you restore a backup it overwrites the data thats is in its way.

Hope I made sence and hope I helped:)

---

### Post by sofasurfer on 2008-05-28
Ok, I'm trying to use Partimage. But when I try to enter the name of a "Image file to create/use", I am not able to type anything in the text box. What am I missing or what did I do wrong?

---

### Post by sofasurfer on 2008-05-28
Never mind. I asked the above question at the thread "Howto: Backup with Partimage" in the "tutorials and tips" forum.

---

