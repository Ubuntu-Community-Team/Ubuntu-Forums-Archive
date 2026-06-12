---
title: "Disable NTFS Write?"
date: 2008-03-19
forum: General Help
---

### Post by nonfiction330 on 2008-03-19
Hello

I was wondering if there's a way to disable the NTFS write support in Gusty.  I know that Gusty comes with NTFS write support by default.  But I like it so Linux doesn't have write access to NTFS drives like back Feisty Fawn and the older version.

I tried to use ntfs-config tool but I could not get it to work with external usb drives, it worked for internal drives, but not external.

I tried to mount the drive as read-only but that only made the files to be read-only not the drive itself.  Also I have a lot of external drives and it be a pain to make each and everyone of them read only.

I prefer like the older version of ubuntu (or other distro linux) where you can only read the drive and not be able to write to it.  (If you right click on the drive you should not be able to have the option of creating any files or folders.

I also tried to remove the ntfs-3g package but that also removes read support.

So I just want to keep read support and don't want write support.

Help Anyone?

---

### Post by mk1w86 on 2008-03-19
If you find where the drive is mounted e.g. /media/harddisk1 then change the permissions of the folder you mounted it on so no one can write to it.
Run

sudo chmod a-w [put the mount point of the hard drive here]

or 

sudo chmod -r a-w [put the mount point of the hard drive here]
to change the permissions of all the folders+files on the drive.

e.g. sudo chmod -r a-w /media/harddisk1

Although I would have thought mounting the filesystem read only should not allow any writes to it.

---

### Post by nick_h on 2008-03-19
> Although I would have thought mounting the filesystem read only should not allow any writes to it.
Yes, I think that is what it should do.  It would also appear to be the simplest solution for the OP.

---

### Post by nonfiction330 on 2008-03-20
> **mk1w86 said:**
> If you find where the drive is mounted e.g. /media/harddisk1 then change the permissions of the folder you mounted it on so no one can write to it.
Run

sudo chmod a-w [put the mount point of the hard drive here]

or 

sudo chmod -r a-w [put the mount point of the hard drive here]
to change the permissions of all the folders+files on the drive.

e.g. sudo chmod -r a-w /media/harddisk1

Although I would have thought mounting the filesystem read only should not allow any writes to it.


I'll give it a try.

Thanks

---

