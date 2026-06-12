---
title: "Mounting and accessing ntfs drives"
date: 2015-08-19
forum: General Help
---

### Post by kristian-knarvik on 2015-08-19
I just went from windows 10 to ubuntu. I have four extra hdds in my system which all are ntfs formatted. I can view the drives fine, but I need to go to the file viewer for the drives to mount. I also have a webserver on one of the drives and I am struggeling giving apache permission to read it. So, the question: What shold I do to correctly mount the drives as internal drives, and why won't apache read from the drive?

Apache is looking at: /media/username/drivename/folder for the web files, but the apache error log says it doesn't have search permissions somewhere between disk root and /media/username/drivename
Can anyone help me? Or is it easier just to return to windows?

---

### Post by HermanAB on 2015-08-19
Simple really.  Don't use NTFS on Linux, unless you have too much hair and won't mind losing a whole bunch of it.

---

### Post by Morbius1 on 2015-08-19
> media/username/drivename/folder
Don't know anything about apache but the problem is /media/username. When you don't mount something in fstab the system will automount it under /media/username. But the system applies an Access Control List to /media/username such that only "username" can access whatever is beyond it.

You will need to have the ntfs partitions mount at boot ( fixing the "but I need to go to the file viewer for the drives to mount" problem ) and mount it somewhere other than under /media/username.

*** Create a mount point - example:
```
sudo mkdir /media/ntfs1
```
*** Run the following command to find the correct UUID number for your partitions:
```
sudo blkid -c /dev/null
```
*** Edit /etc/fstab and using the following template add a line to the end of the file - with the correct UUID number:
```
UUID=DA9056C19056A3B3 /media/ntfs1 ntfs defaults,nls=utf8,umask=000,uid=1000,gid=1000 0 0
```
*** If you have mounted the partition through the file manager unmount it.

*** Then remount it with this command:
```
sudo mount -a
```

This will mount the partition with you as owner ( uid=1000, assuming your user id is 1000 ) and with you as group ( gid = 1000 ). It will also make it so that it's world accessible as read and write ( umask=000 ) so depending on who and how you are accessing this partition you might want to adjust that.

umask represents the permissions you want to remove from the ntfs defaults which are 777. So to make it accessible only to you for example you can make it umask=007. To make it accessible only to you and members of say ... the plugdev group ... the line would look something like this:
```
UUID=DA9056C19056A3B3 /media/ntfs1 ntfs defaults,nls=utf8,umask=007,uid=1000,gid=plugdev 0 0
```

NTFS partitions in Linux are mounted as "views" using fuse so permissions are the same throughout the partition and are immutable so you can't change permissions on a particular file or folder withing the partition.

[COLOR=#0000cd]**EDIT**[/COLOR]: Might as well give another example. Let's say you want to give r/w access to yourself but only read access to group plugdev:
```
UUID=DA9056C19056A3B3 /media/ntfs1 ntfs defaults,nls=utf8,umask=027,uid=1000,gid=plugdev 0 0
```
The resulting ntfs partition will mount with permissions of 750. Writeable to you, readable only to plugdev group members, and inaccessible to everyone else.

---

