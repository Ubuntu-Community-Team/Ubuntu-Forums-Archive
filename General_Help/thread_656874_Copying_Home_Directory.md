---
title: "Copying Home Directory"
date: 2008-01-03
forum: General Help
---

### Post by sekinto on 2008-01-03
I'm trying to copy my personal directory (inside my home directory) to an external hard drive. But when I do so this error appears frequently:

error "operation not permitted" while copying (file name).(extension)

How do I fix this?

---

### Post by ~LoKe on 2008-01-03
Is your external harddrive mounted to /media/something?  You'll need to use sudo.

---

### Post by sekinto on 2008-01-03
I'm still getting the error even when using "sudo nautilus".

---

### Post by ~LoKe on 2008-01-03
> **sekinto said:**
> I'm still getting the error even when using "sudo nautilus".

Try using the terminal, I hate using gksu and nautilus.

```
sudo cp -R /home/USERNAME /media/location
```

---

### Post by sekinto on 2008-01-03
Now I get:
cp: cannot create symbolic link `/media/HD-HCU2/Backup/anthony/Examples': Operation not permitted

And /anthony/Examples was the first thing that wouldn't copy when using nautilus to.



EDIT:
Now I'm starting to get a lot of "Cannot create regular file" errors to.

---

### Post by teryowen on 2008-01-03
perhaps the exeternal was mounted as ro instead of rw try remounting it with rw

---

### Post by ~LoKe on 2008-01-03
> **teryowen said:**
> perhaps the exeternal was mounted as ro instead of rw try remounting it with rw

Yep.  Give us the output of...
```
cat /etc/fstab
```
You might need to make the change there.

---

### Post by TreeFinger on 2008-01-03
You can not copy a hard link type of file to another storage medium. You need to copy the regular files/ directory files that are not hard links. To copy something that is a hard link you need to go to where the link is directing to. You can find out what files are links and where they point to by typing 'ls -l ~' at the terminal.

I am not sure if there is a more efficient way of going about this. I am just beginning to learn about using Unix/Linux. I can assure you the reason I gave for why this isn't working is the true problem, although there may be a better way then the way I suggested of actually copying the link files.

----edit

I am confused if you are trying to copy your entire home dir (~) or just the Examples file(~/Examples) in your home dir?

---

### Post by sekinto on 2008-01-03
Output of cat /etc/fstab
[INDENT]```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=362caabf-bcdd-41f4-8334-e0fbce67de3c /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=3A922961409519EE /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=f6da2da6-37b8-40e0-a3a0-4de6e6d1445c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```[/INDENT]

---

### Post by teryowen on 2008-01-03
Hey, i dont even see your external unless its the hda1 which is weird.

but if the external is hda1 try this.

sudo umount /dev/hda1
sudo mount -rw /dev/hda1 /media/hda1

if the external is sda1 or whatever else replace hda1 accordingly. see if this works.

---

### Post by TreeFinger on 2008-01-03
I don't know why you people have him messing around with mounts..

A hard-link type file can not span file systems.. it must stay on the original file system. It is a HARD LINK

That is the problem.

---

### Post by teryowen on 2008-01-03
he is copying a folder from his /home/* where the * is the folder his copying. wats the problem?

---

### Post by TreeFinger on 2008-01-03
> **teryowen said:**
> he is copying a folder from his /home/* where the * is the folder his copying. wats the problem?


If the file is a hard-link type file it can not be copied to another file system. That is the problem. Nothing to do with mounts.


If the ~/Examples dir is not a hard-link type file then I am wrong, but I am pretty sure it is.

---

### Post by teryowen on 2008-01-03
ok so if its not mounts, and if you say the file is hard-link then this should work:

sudo cp -R /home/USERNAME/* /media/location/folder

---

### Post by sekinto on 2008-01-03
No, I'm possitive hda1 isn't my external hard drive.

---

### Post by kpkeerthi on 2008-01-03
Perhaps its an USB drive (?). That explains why it is not in FSTAB.

---

### Post by sekinto on 2008-01-03
Yes, it is USB.

---

### Post by TreeFinger on 2008-01-03
> **sekinto said:**
> No, I'm possitive hda1 isn't my external hard drive.


Who are you talking to? Where are you trying to copy the files? If you are trying to copy files to another file system (something in /media) you can not copy hard-link files. Unless there is an argument that will fix this. I'm sure there is an easy way around this, but I do not know what it is.

The only place you will be able to copy files that are hard-link type are in your current root dir, not a mounted device (another hd, another partition, a CD-R, a USB drive).

---

### Post by sekinto on 2008-01-03
So how can I back up my files?

---

### Post by kpkeerthi on 2008-01-03
As treefinger says hardlinks cannot be copied across file systems.

Just confirm if /anthony/Examples is a hard link.

If it is a directory, use...
 
```

ls -ld /anthony/Examples

```

else use...
```

ls -l /anthony/Examples

```

and post back the results.

---

### Post by TreeFinger on 2008-01-03
> **sekinto said:**
> So how can I back up my files?

I haven't gotten that far in my book yet. :)

I'll wait until you confirm it is a hard-link on your system. 



It may not be the problem, but I do not see what else it could be if you are able to view the contents and write to your USB drive.

---

### Post by sekinto on 2008-01-03
But it isn't just that directory, to run that check on every directory and file that there was a problem with would take forever.

---

### Post by TreeFinger on 2008-01-03
OK, I skipped ahead in my book to the back-up Chapter.

The quickest way to backup your home dir would be to type this at the terminal:

```

tar -cvf /location/of/your/USB/drive ~

```

I just did it on my system. Everything located in your home dir will be inside that tar file.

---

### Post by sekinto on 2008-01-03
I'm such a moron, how could I not think of that.

---

### Post by ~LoKe on 2008-01-03
> **TreeFinger said:**
> OK, I skipped ahead in my book to the back-up Chapter.

The quickest way to backup your home dir would be to type this at the terminal:

```

tar -cvf /location/of/your/USB/drive ~

```

I just did it on my system. Everything located in your home dir will be inside that tar file.

That preserves permissions and all, correct?  How about symbolic links?

---

### Post by TreeFinger on 2008-01-03
> **~LoKe said:**
> That preserves permissions and all, correct?  How about symbolic links?

I can not answer your questions. Do not assume that is preserves permissions, etc. I am not sure.

---

### Post by ~LoKe on 2008-01-03
Hm...from **man tar** (that sounds dirty)
> -p, --same-permissions, --preserve-permissions
So if you add the p flag it should preserve permissions...nice.

---

