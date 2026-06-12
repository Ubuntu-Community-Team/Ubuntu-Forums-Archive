---
title: "Can't remove a directory"
date: 2007-02-28
forum: General Help
---

### Post by z987k on 2007-02-28
This is weird, I'm trying to remove an empty directory as root, but can't.
```
zach@zach-desktop:/media/hde1/Music/albums$ sudo rmdir Strata/
rmdir: Strata/: Operation not permitted

```

um, wtf?  So i looked at the permissions and user is 1233323002 and group is 66734443
SELinux content: unknown

So I have no idea what happened there.  There is no user like that and root can't get rid of it so I'm a little lost.

---

### Post by firefly2442 on 2007-02-28
I'm not sure but I think this is because whatever you are trying to delete is in a mounted partition.  Ubuntu automatically mounts CDs and other media.  If you are trying to delete a file on a CD that is mounted, this obviously will not work.

---

### Post by z987k on 2007-03-01
Of course it's mounted, you can't read the filesystem if it's not.
Also it's a regular HDD, hence the hde1

---

### Post by aysiu on 2007-03-01
You're saying that inside of /media/hde1/Music/albums, there's a folder called Strata, which is an empty folder, and you want to delete that folder?

In other words, the folder is /media/hde1/Music/albums/Strata?

If so, what partition type is /media/hde1 (NTFS, FAT32, Ext3, Reiserfs)? And what options is it mounted with in your /etc/fstab file?

---

### Post by zanglang on 2007-03-01
How about if you used "sudo rm -rf" instead? Do you have write-access to that partition?

---

### Post by yabbadabbadont on 2007-03-01
Change the user, group, and permissions to sensible values, then remove the directory.  (assuming it is empty of course)

Edit: Way too slow!  :lol:

---

### Post by z987k on 2007-03-01
Empty folder, hdde is automounted with defaults, partition type ext3
```
zach@zach-desktop:/media/hde1/Music/albums$ sudo chown zach Strata/
chown: changing ownership of `Strata/': Operation not permitted

```

```
zach@zach-desktop:/media/hde1/Music/albums$ sudo chmod 777 Strata/
chmod: changing permissions of `Strata/': Operation not permitted

```

---

### Post by mack75 on 2007-03-01
What's the filesystem??

The uid and gid are too high.

Try mounting the partition with:
mkdir /mnt/tmp && mount -t [filesystem_type] -o uid=0 /dev/hde1 /mnt/tmp

For some filesystems Linux don't have support to write.

Regards

---

### Post by aysiu on 2007-03-01
> **z987k said:**
> Empty folder, hdd is automounted with defaults, partition type ext3 **Step 1**:
If you're using Ubuntu, type ```
gksudo nautilus
``` If you're using Kubuntu, type ```
kdesu konqueror
``` If you're using Xubuntu, type ```
gksudo thunar
``` This command will open the file browser as root. 

**Step 2**
Once it's open, press Control-L

**Step 3**
Type ```
/media/hde1/Music/albums
``` then hit Enter. 

**Step 4**
Right-click the Strata folder and delete it.

---

### Post by z987k on 2007-03-01
would the uid=0 override all other permissions set?

Yes, I noticed the uid and gid are way high.

Also, to aysiu, notice sudo rmdir didn't work either.  Basically root permissions are not allowing this to be deleted, like I need a supersuperuser, lol.

---

### Post by yabbadabbadont on 2007-03-01
Check the owner, group, and permissions on the parent directory to be sure that they are not messed up too.

---

### Post by z987k on 2007-03-01
They're not, but a couple of other empty folders in the same directory are messed up.

Also, I can't seem to mount the filesystem uid=0 whats up with that?

---

### Post by zvacet on 2007-03-01
```
sudo -i
```
```
cd /media/hde1/Music/albums
```
```
rm -r foldername
```

---

### Post by z987k on 2007-03-01
ok, seriously people being root doesn't do anything for deleting this folder.

I think I'm going to have to transfer everything to a different hdd and format if I ever want to get rid of this thing.

---

