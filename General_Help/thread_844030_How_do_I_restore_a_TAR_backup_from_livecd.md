---
title: "How do I restore a TAR backup from livecd"
date: 2008-06-29
forum: General Help
---

### Post by sofasurfer on 2008-06-29
I have done a backup with... ```
tar cvpcf imagebackup.tgz (excluded various files) / 
```

I have 2 questions...

#1) When I run the restore command... ```
tar xvpfz imagebackup.tgz -C / 
```
the files in the backup are returned to the working system. However, I would like to have the system replaced, meaning that I would like to see files that were added to the system AFTER the backup was made, eliminated.
Example... I backup files 1, 2 and 3. Then I add file 4 to system. Now when I restore I want files 1, 2 and 3 returned but I also want 4 to be gone. Is this possible.

#2) I can not accomplish a restore from a livecd. Under livecd I run 'disk mounter' to mount my primary drive and my backup drive. I can do a 'ls /media/disk-1' and see the contents of my primary drive. But when I do a 'ls /media/disk' the only thing I see on my backup drive is 'lost+found' which does not exist on my backup drive. My backup file, 'imagebackup.tgz' does not appear.
Why?

If I could do this much I think my next step would be to...

```

sudo su
cd /media/disk (my backup drive)
tar xvpfz imagebackup.tgz -C /media/disk-1/ (my working system drive)

```

I am not sure that my path in the tar line would be correct.

Can anyone help me cross this final hurdle to a successful restoration?

---

### Post by logos34 on 2008-06-29
> **sofasurfer said:**
> But when I do a 'ls /media/disk' the only thing I see on my backup drive is 'lost+found' which does not exist on my backup drive. My backup file, 'imagebackup.tgz' does not appear.
Why?

this happens to me, and I have to change ownership. So try:

sudo chown username /media/disk/imagebackup.tgz

(I guess I should add that that in my case it's k3b that can't see it until I go back and change ownership--only then can I burn it to disc.  But in my case at least it shows up in the terminal with ls...not sure why you can't see yours.  Maybe try unmounting the disk and remounting manually as root:

sudo umount /media/disk

sudo mkdir /media/backup_disk

sudo mount -t [fs type] /dev/[drive] /meda/backup_disk

---

### Post by p_quarles on 2008-06-29
On your first question: check out rsync (and its graphical front-ends, such as grsync). This can be used to create and restore mirrors of directories/trees, and can be set to delete files that are not present in the source directory.

---

### Post by sofasurfer on 2008-06-29
Regarding question #2...

I downloaded a knoppix livecd to try and was unable to get it to boot. So I downloaded a slax livecd. I found the same problem that I stated above in question #2. I was not able to view the contents of my backup drive. But then I found that I needed to browse through the file system as thus...

livecd/mnt/sda1/media/backupdrive. This got me what I needed but I am sure there must be an easier way. The confusion with this method will surely lead to a disaster eventially.

Anyway, now I will try the process again with the ubunto livecd.

Thanks.

---

### Post by sofasurfer on 2008-06-29
I was able to restore my system using the method stated above. You must follow the file system from the livecd to the target drive. 
I wonder if I should have unmounted my drives before I installed the livecd. O well, I accompliched what I wanted

---

### Post by sofasurfer on 2008-06-29
I am now able to restore my files easily with tar. I have not actually had to restore a trashed system yet. So if I reformat my / partition will I really be able to bott after I restore it with tar? Is the mbr within the / partition? I have much info on mbr and booting but I still have not gotten my brain around it enough to feel like I understand any of it.

---

### Post by logos34 on 2008-06-29
> **sofasurfer said:**
> I was not able to view the contents of my backup drive. But then I found that I needed to browse through the file system as thus...

livecd/mnt/sda1/media/backupdrive. This got me what I needed but I am sure there must be an easier way.
> 
I was able to restore my system using the method stated above. You must follow the file system from the livecd to the target drive. 
I wonder if I should have unmounted my drives before I installed the livecd. 

The drives are unmounted automatically when you reboot...I don't understand why you were having trouble accessing the backup drive the first time.. '/media/disk' is the default path.  

The Master Boot Record is separate, on the first sector of hard disk.  As long as you don't change the partitions, you should be able to boot a restored /.

---

