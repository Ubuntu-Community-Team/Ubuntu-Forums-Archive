---
title: "Copy a Folder's data to a Folder in another partition, questions."
date: 2014-11-17
forum: General Help
---

### Post by mikodo on 2014-11-17
I am amalgamating my data from an old install, to the current one. From old install (10.04) to (12.04).

I have settled on using cp -a for moving the data. I don't want the target folders (12.04), to have the parent folder (10.04) names in them. 

Here is an example command for my Documents folders.  Does this syntax look correct? Notice the wild card. 

```
cp -a /dev/sda5/home/mikodo/Documents/*** **/dev/sda8/home/mikodo/Documents/
```
Also, should I use the UUID's for either or both, instead of /dev/sda5/8?

After mounting both partitions, I'll follow your directions and then play around with them, using expendable data first, to check. 

Thank you.

---

### Post by JKyleOKC on 2014-11-17
I would mount both devices -- first creating mount points such as /mnt/home5 and /mnt/home8 -- and then copy from the mount points, not from the actual devices. The mounting step is, I believe, necessary to make the filesystems compatible with utilities such as "cp" and the like. Only when doing raw reads and writes such as with "dd" (aka Data Destroyer) is it advisable to use the actual devices under "/dev"...

---

### Post by mikodo on 2014-11-17
> **JKyleOKC said:**
> I would mount both devices -- first creating mount points such as /mnt/home5 and /mnt/home8 -- and then copy from the mount points, not from the actual devices. The mounting step is, I believe, necessary to make the filesystems compatible with utilities such as "cp" and the like. Only when doing raw reads and writes such as with "dd" (aka Data Destroyer) is it advisable to use the actual devices under "/dev"...

All right. I am glad I asked here.

---

### Post by mikodo on 2014-11-17
I will be moving the folders to my current install, (12.04).

So, I should just have to mount the old install, (10.04). Right?
> sudo mount /dev/sda5 /mnt
and then use
> cp  -a /mnt/dev/sda5/home/mikodo/Documents/* /home/mikodo/Documents/
I think there is supposed to be a trailing "/" after the destination directory/folder. I know there must be one with Rsync, to copy into the last directory, so probably it is the same with the cp command.

Nevertheless, I will play with disposable files/folders/directories using cp, to be sure.

---

### Post by coldcritter64 on 2014-11-17
> ```
cp -a /mnt/dev/sda5/home/mikodo/Documents/* /home/mikodo/Documents 
```
If you've mounted your (edit: old 10.04) home partition (/dev/sda5) on /mnt that command should look more like,
> ```
cp -a /mnt/home/mikodo/Documents/* /home/mikodo/Documents                      
```

The home folder is usually on the root of the partition it is located on. /dev/sda5 in this case is the actual device it is on, not part of the path.

---

### Post by mikodo on 2014-11-17
> **coldcritter64 said:**
> If you've mounted your (edit: old 10.04) home partition (/dev/sda5) on /mnt that command should look more like,


The home folder is usually on the root of the partition it is located on. /dev/sda5 in this case is the actual device it is on, not part of the path.
Thank you.

Do I need a trailing "/" on the destination. Like: Documents/ or not?

---

### Post by coldcritter64 on 2014-11-17
Wouldn't hurt to put one there, I usually do. But I *think* it will be ok without it.

---

### Post by mikodo on 2014-11-17
> **coldcritter64 said:**
> Wouldn't hurt to put one there, I usually do. But I *think* it will be ok without it.
Thank you.

The idea of the wild card * is to just copy the data in the source folder, to the destination folder. Not put another "Documents" inside of the destination Documents folder.

But, I will try as you say.

---

### Post by coldcritter64 on 2014-11-17
That wildcard, how you have it, should do exactly as you want as it specifies the contents of the old Documents folder only and not the source "Documents" folder itself by using it like that. That should work OK, provided the *destination* Documents folder is an empty one or no files/folders being copied already exist at the destination.

The -a switch according to man cp also covers recursive copying  (same as -dR) so any sub folders and contents will also be copied. It looks good.

---

### Post by mikodo on 2014-11-17
> **coldcritter64 said:**
> That wildcard, how you have it, should do exactly as you want as it specifies the contents of the old Documents folder only and not the source "Documents" folder itself by using it like that. That should work OK, provided the *destination* Documents folder is an empty one or no files/folders being copied already exist at the destination.

The -a switch according to man cp also covers recursive copying  (same as -dR) so any sub folders and contents will also be copied. It looks good.
Thank you, for the help.

I know what to do now. 

Regards.

---

