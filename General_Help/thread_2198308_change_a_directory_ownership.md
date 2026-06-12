---
title: "change a directory ownership"
date: 2014-01-08
forum: General Help
---

### Post by userau101 on 2014-01-08
Hi,
I have created a directory called data under following path:
```
/media/storage/data
```
Currently the data directory is owned by root.
```
drwxrwxrwx 1 root root    0 Jan  8 22:18 data
```
I want to change this from root to www-data.
I used following command:
```
chown www-data:www-data /media/storage/data
```
When i do ls -lh i still see that the data directory still belongs to root and there is nothing changed.

The directory currently is empty but i will put files in the drectory later on.

How do i change this from root to www-data for this directory.

Thanks

---

### Post by coffeecat on 2014-01-08
Are you using /media/storage/data as a storage folder or as a mountpoint? /media/storage/data would be an odd choice for a data storage folder because everything in /media is intended to be used as a mountpoint.

I'll assume for now you are using /media/storage/data as a mountpoint. Changing the ownership/permissions of a mountpoint folder if nothing is mounted to it would be a waste of time, because the ownership and permissions of the mounted filesystem would take precedence when mounted.

Mount whatever filesystem/device you wanted mounted to /media/storage/data, and then run your chown command. This chowns the mounted filesystem, not the mountpoint. If you then run ls -lh before unmounting, you'll see that it appears to be owned by www-data:www-data. Unmount the filesystem from /media/storage/data, re-run ls -lh and you'll see ownership of /media/storage/data by root - which you can safely disregard. If you are still dubious, remount to /media/storage/data, run ls -lh yet again and you should be re-assured.

If, however, you are using /media/storage/data as a simple storage folder, you need to prepend your chown command with sudo - as you would for what I describe above.

---

### Post by Impavidus on 2014-01-08
If you use it as a mountpoint and you have mounted something there, on what kind of partition is the mounted file system?

---

### Post by userau101 on 2014-01-08
> **coffeecat said:**
> Are you using /media/storage/data as a storage folder or as a mountpoint? /media/storage/data would be an odd choice for a data storage folder because everything in /media is intended to be used as a mountpoint.

I'll assume for now you are using /media/storage/data as a mountpoint. Changing the ownership/permissions of a mountpoint folder if nothing is mounted to it would be a waste of time, because the ownership and permissions of the mounted filesystem would take precedence when mounted.

Mount whatever filesystem/device you wanted mounted to /media/storage/data, and then run your chown command. This chowns the mounted filesystem, not the mountpoint. If you then run ls -lh before unmounting, you'll see that it appears to be owned by www-data:www-data. Unmount the filesystem from /media/storage/data, re-run ls -lh and you'll see ownership of /media/storage/data by root - which you can safely disregard. If you are still dubious, remount to /media/storage/data, run ls -lh yet again and you should be re-assured.

If, however, you are using /media/storage/data as a simple storage folder, you need to prepend your chown command with sudo - as you would for what I describe above.

Hi thanks for the reply.
Here is more details on what i am trying to achieve and hopefully answers some of your questions/assumptions above.
In my server I have two physical HDDs. The /media/storage is a mountpoint for the second HDD (/dev/sdb1). It has a single partition formatted as NTFS. I have line in fstab which mounts this partition on bootup so this is always mounted, i.e. /dev/sdb1 has a mount point of /media/storage. There are already files on this partiiton under /media/storage. I have not created a folder called data under /media/storage/data and would like this folder to have ownership of www-data. I am not sure how to achieve this, i.e. change ownership or is it not possible because this folder is under a mountpoint even though this mountpoint will always exist. Does that help?

Thanks

---

### Post by coffeecat on 2014-01-08
If I'm following you correctly, a couple of points.

If you make a folder called data in /media/storage before you mount /dev/sdb1 to /media/storage it will simply become inaccessible and seem to disappear when you mount /dev/sdb1 to /media/storage. If you create /media/storage/data after you have mounted /dev/sdb1 to /media/storage, then the "data" folder will be in the /dev/sdb1 filesystem and not a true subfolder of /media/storage.

You cannot change permissions/ownership of NTFS with chmod and chown because it is a Microsoft filesystem which does not support Unix/Linux permissions. You need to set ownership and permissions through your mount options in /etc/fstab, which are applied globally.

---

### Post by Morbius1 on 2014-01-08
First, what coffeecat said. 

You can change ownership of the entire partition to www-data:www-data but that may not be workable.

You could however use bindfs to create another "view" of this subfolder:

**** Install bindfs:
```
sudo apt-get install bindfs
```
**** Then create a new directory called data under /media:
```
sudo mkdir /media/data
```
**** Then as a test run this command to mount /media/storage/data to /media/data with new ownership:
```
 sudo bindfs -o perms=0660:+X,force-group=www-data /media/storage/data /media/data
```
[COLOR=#0000cd]* You never stated what version of Ubuntu you are using. "force-group" is the new option but for older versions it's just "group"*[/COLOR]

If that works for you you can add the line - without sudo - above the "exit 0" line in /etc/rc.local so that it happens on every boot.

But there will be a performance hit to all this but it depends on how you are using it. An NTFS partition in Windows is faster than on Linux becasue Linux creates a "view" of the partition using a virtual file system. Bindfs also creates a "view" using the same kind of virtual file system so you end up with a view of a view.

---

