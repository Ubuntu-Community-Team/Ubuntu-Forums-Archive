---
title: "Using dd for image backup results in oddly large file size"
date: 2015-12-02
forum: General Help
---

### Post by ben187 on 2015-12-02
Once a month, booting from a Ubuntu 15.10 disk in 'try Ubuntu', I make an image backup of my unmounted /home (/dev/sdd1), which is in it's own partition, to a mounted file system DiskImages.

I use this command: dd if=/dev/sdd1 conv=sync,noerror bs=64K | gzip -c >/media/DiskImages/Home.img.gz

This takes about 4 hours.

The utility "GParted" shows this partition (/dev/sdd1) to be 'ext4', with a size of 585.94 GiB on a 1.25Tib disk.  The 'used' value of "/home" (/dev/sdd1) is 149.62 GiB, while the 'unused' size is 436.32 GiB.

So, GParted is saying I'm currently using about 150 GiB.

However, when I look at the file Home.img.gz using the 'Files' utility icon on the Ubuntu launcher bar, it shows the Home.img.gz file size to be 231 GB!  That's about 80 GB larger than the original partition!

But the part that is most odd, is if I open up the Home.img.gz file with the "ArchiveManager" utility, it shows Home.img (as expected) with a file size of 2.1 GB!  That's 1% of the file size of Home.img.gz!

So, in summary, I've got wildly differing file sizes:

145 GB used on /Home partition via GParted
231 GB for Home.img.gz via Files utility
2.1 GB Home.img via ArchiveManager

Totally not what I was expecting!

Can anyone shed any light on this oddity?

Thanks!

---

### Post by The Cog on 2015-12-02
>  That's about 80 GB larger than the original partition!
No. As I understand your post, you say the original partition size is 585.94 GiB.
dd reads the entire partition, not just the used (written on) part but all of it. 

As for the archive manager part, I'm not sure. Maybe it can't cope with zipped files that large. 
What does this say?:
```
gzip --list /media/DiskImages/Home.img.gz
```

If possible, try uncompressing the zip file and see what size the output is. Failing that, use
```
gunzip -c | wc -c
```
to count how many bytes are produced by decompression.

P.S. 
If you are just archiving an ext4 partition then parhaps using the tar utility would be better. If you run the tar command as root, it can read/save all files regardless of permissions. It only reads the used partition content, and has an inbuilt compression option. You can restore to different sized partitions too. Tar needs the partition to be mounted.

Or if you don't want to mount first, look at fsarchiver which again only archives the used portion of the partition, and can restore to different sized partitions (given enough space).

---

### Post by ben187 on 2015-12-02
"The Cog", thanks for your reply.  You are correct, the total partition size is [COLOR=#000000]585.94 GiB.

[/COLOR]Here's the info from gzip --list (doesn't appear that gzip has a 'human' option for size, so I've inserted commas)

```
         compressed                 uncompressed         ratio uncompressed_name
         231,813,593,039          2,080,374,784         -11042.9% Home.img
```

Clearly, for whatever reason, the compression isn't helping - it's causing a problem!  

regarding using tar:
I have a VirtualBox on my account under home, with a guest valid Windows 7 system on it.  When I have tried to use backups of the VirtualBox system in the past, then the Windows guest will complain that it isn't a valid install, and shut it down.  Using dd and creating the image, I can move it to new hard drives when I need to.  I do use tar for my daily and weekly backups of my system.  Thanks for the suggestion on this tough!

I'll try your suggestion regarding running without gzip this evening, when I can take the time to shut down my /home partition.

Thanks!

Ben

---

### Post by ben187 on 2015-12-02
Looks like my post stripped out the spaces on the output from gzip --list, making it hard to read, so reposting:

Compressed
[COLOR=#000000]231,813,593,039

Uncompressed
[/COLOR][COLOR=#000000]2,080,374,784

[/COLOR][COLOR=#000000]ratio:
[/COLOR][COLOR=#000000]-11042.9% 

name:
Home.img[/COLOR][COLOR=#000000]


[/COLOR]

---

### Post by coffeecat on 2015-12-02
> **ben187 said:**
> Looks like my post stripped out the spaces on the output from gzip --list, making it hard to read, so reposting:

You need to use BBCode code tags to preserve formatting like that. I've edited your post accordingly.

By the way, I notice you are adding [noparse][COLOR=#000000][/COLOR][/noparse] tags all over the place in your posts. I guess you are clicking on the text colour button in the toolbar. You don't have to. The forum defaults text to black (#000000) for you.

---

### Post by ben187 on 2015-12-02
No, I'm not clicking on any buttons at all, other than the "Post Quick Reply" button.  I'm posting it in the 'Quick Reply" input field.

thanks for the 'BBCode" info.

---

### Post by sudodus on 2015-12-02
> **ben187 said:**
> Once a month, booting from a Ubuntu 15.10 disk in 'try Ubuntu', I make an image backup of my unmounted /home (/dev/sdd1), which is in it's own partition, to a mounted file system DiskImages.

I use this command: dd if=/dev/sdd1 conv=sync,noerror bs=64K | gzip -c >/media/DiskImages/Home.img.gz

This takes about 4 hours.

...

***dd*** is a very powerful tool, but ***risky***, because it does what you tell it to do without questions. So if you tell it to wipe the family pictures, it will do it. A minor typing error is enough to destroy your data. Enough with warnings.

- dd can do the job as you described. ***gzip*** can do the compression and ***gunzip*** can uncompress before restoring with dd 'the other way'.

-  But gzip does not report the size of huge compressed files correctly. If you use ***xz*** the report will be correct up to much larger sizes, but I think xz is way too slow for your kind of backup job.

-  dd copies all data of a drive or partition. If you overwrite all unused drive space with zeros, the compressed image will be much smaller (because the patches with zeros will compress very well). But the overwrite process is slow and will add hours to the backup process.

-o-

I would recommend that you use another tool, [Clonezilla](http://clonezilla.org), instead of dd + gzip. Download a 'stable' iso file and make a CD disk or USB boot drive.

- Clonezilla has a user interface that helps the user read and write to the correct places both at backup and restore. It is ***safer*** to use.

- Clonezilla can clone as well as create a compressed image (a number of compressed files in a directory). It can make images of a whole drive as well as of a single partition or group of partitions.

- ***Clonezilla does not backup unused data blocks***, so the process will be faster, and the size of the backup image will be smaller than what dd can do.

Finally, before you discard your old 'dd backup files' you should ***test that you can restore*** your home partition from the Clonezilla backup.

---

### Post by ben187 on 2015-12-02
OK, thanks!

---

