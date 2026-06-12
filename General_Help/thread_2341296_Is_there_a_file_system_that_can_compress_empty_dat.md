---
title: "Is there a file system that can compress empty data in files"
date: 2016-10-26
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2016-10-26
By empty data i mean lets say i take a 4GB flash drive and put 2GB data on it
i then make a disk image file (eg backup.img) from it using dd it will give me a 4GB file
is there a file system that would make said file be treated as a 2GB file instead of a 4GB file thus only use 2GB of disk storage
i know you can compress it in say .zip or tar.gz but it takes time to decompress the file

---

### Post by TheFu on 2016-10-27
Interesting question.  All that comes to mind is a qcow2 container for the file system or cramfs.  There's a file system comparison on wikipedia - have you checked that? It lists jffs2 and btrfs and zfs and zfs+ as options. Never used any except ZFS (only on Solaris).

Or ... don't use imaging to make backups. Use something like partimage or a file-based backup solution. This comment is based only on "backup.img" in the OP.  If you use dd, it WILL always show 4G. That is kinda the point of dd, right?

---

### Post by sudodus on 2016-10-27
***Clonezilla*** creates images, where only used blocks are copied, so it sort of does what you ask for. It means that the process will be faster, and also that the image will be smaller. (There is also compression of the data from the used blocks.)

Clonezilla uses ***partclone***, which is more modern than partimage. If I remember correctly, you need partclone for ext4. I don't know about other linux file systems. partclone can also backup NTFS and FAT32.

[clonezilla.org](clonezilla.org)

But as TheFu wrote, you can use a file-based backup solution.

[Backup Your System](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by pqwoerituytrueiwoq on 2016-10-27
> **TheFu said:**
> Interesting question.  All that comes to mind is a qcow2 container for the file system or cramfs.  There's a file system comparison on wikipedia - have you checked that? It lists jffs2 and btrfs and zfs and zfs+ as options. Never used any except ZFS (only on Solaris).

Or ... don't use imaging to make backups. Use something like partimage or a file-based backup solution. This comment is based only on "backup.img" in the OP.  If you use dd, it WILL always show 4G. That is kinda the point of dd, right?
preferably i would like it to show 4gb as the file size but only use 2gb on the disk, not sure how a file manger would handle that, but anywa
it was not only for image files, but they are a good example i have a pile of old cd images
was hoping for something that would compress empty data kinda like how the sandforce controllers do on SSDs with data transfers

---

### Post by sudodus on 2016-10-28
Maybe you can use [squashfs](https://en.wikipedia.org/wiki/SquashFS), which is used in the linux iso files and expanded to RAM when running a live session.

---

### Post by pqwoerituytrueiwoq on 2016-10-28
Is there a way to add files to a squashfs? or would it need to be rebuilt?
given the max fs size i assume the entire fs does not need to be on ram

edit:a unisonfs looks to be what i want (well close enough)
[http://tldp.org/HOWTO/SquashFS-HOWTO/creatingandusing.html#sqwrite](http://tldp.org/HOWTO/SquashFS-HOWTO/creatingandusing.html#sqwrite)
this seems to take a squashfs mount point and a normal folder and merge them into one folder

I found a command to compress at a higher density,[FONT=courier new] mksquashfs psx psx.sqsh.xz -comp xz -b 1M[/FONT]
This took 52 minutes compared to about 15min and gave my i5-4690k a good workout, the file was 2 to 3 GB smaller, in total it saved 21.9GB (Not GiB)
53.9GB uncompressed, mostly binary data

---

### Post by sudodus on 2016-10-29
Congratulations and thanks for sharing your solution :KS

---

