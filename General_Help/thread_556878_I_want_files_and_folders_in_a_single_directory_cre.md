---
title: "I want files and folders in a single directory created with 007 mask"
date: 2007-09-21
forum: General Help
---

### Post by Brazen on 2007-09-21
I want one directory that is shared with a bunch of users.  Any files and folders created in the directory should be created with 007 masked permissions (770 for folders and 660 for files).  I've already set the sgid bit on the parent directory so the group will be the same on all files which all these users are a member of.

Is there anyway to set the mask on just a single directory?  I found I can set the system-wide umask by changing it in the /etc/profile directory, but I would rather not do that.  I would rather change it for just files and folders created under this one directory.  Any ideas?

If there is some other way to get a bunch of users to be able to write to everything created in this directory, I'm all ears.

---

### Post by dcstar on 2007-09-21
> **Brazen said:**
> I want one directory that is shared with a bunch of users.  Any files and folders created in the directory should be created with 007 masked permissions (770 for folders and 660 for files).  I've already set the sgid bit on the parent directory so the group will be the same on all files which all these users are a member of.

Is there anyway to set the mask on just a single directory?  I found I can set the system-wide umask by changing it in the /etc/profile directory, but I would rather not do that.  I would rather change it for just files and folders created under this one directory.  Any ideas?

If there is some other way to get a bunch of users to be able to write to everything created in this directory, I'm all ears.

```
man chmod
man chgrp
```

---

### Post by mojoman on 2007-09-22
If I remember correctly you'd need to set sgid in order for the newly created files and folders within that directory to have the correct group ownership.

```
chmod g+s foo
```

So, create a new group. Make sure that every users who you want to have access to this common directory is a member of this group. Make that group the owner of the directory, using chgrp. Than make sure to set sgid as above. And that's it. All files created in that directory will now be accessible to all members of the group, including writing. I have several directories like this in my /home, directories for movies, music etc.

I usually don't refer people to man pages but the man chmod is very useful reading. It takes a while to get the hang of it (well, it took a nitwit like me some time anyway) but it's worth the effort, especially as permissions is a fundamental aspect of Linux.

I too tried the umask at first but I'm not sure it's doable. It might be if you made some sort of bash script but that's beyond me.

best regards
/mojoman

---

### Post by Brazen on 2007-09-22
yeah the sgid bit is already set, so new files and folders belong to the proper group.  The problem is that new files and folders don't get the write permission for the group, plus I want others to get 0 permissions.

Chmod isn't going to be much help there either as that only works for existing files and folders (I guess maybe you should have read the man page ;) ).  I might also add that I know I *can* do this with ACLs, but that adds a layer of complexity that I would rather not have to deal with.

---

### Post by mojoman on 2007-09-22
> **Brazen said:**
> yeah the sgid bit is already set, so new files and folders belong to the proper group.  The problem is that new files and folders don't get the write permission for the group, plus I want others to get 0 permissions.

Chmod isn't going to be much help there either as that only works for existing files and folders (I guess maybe you should have read the man page ;) ).  I might also add that I know I *can* do this with ACLs, but that adds a layer of complexity that I would rather not have to deal with.

Maybe I should read up on the man page, it's been a while, hehe. But seriously, I got this setup and all files and folders created in these directories get read/write permissions for the group. I use this everyday. However, they are also world readable. But apart from they being world readable, it sounds like what you're looking for.

I don't know the first thing about ACL so I can't be of any help there but one suggestion I got when I mucked around with this a while ago was to try to have som short bash script in the fstab. I never figured out just how that would be done though. 

cheers
/mojoman

---

### Post by Brazen on 2007-09-22
> I got this setup and all files and folders created in these directories get read/write permissions for the groupIs it just files under a single directory, or is it all new files on your system?  If you did something in the fstab then I wonder if it's just that one mount point gets read/write permissions (which would be fine with me).  The only caveat would be if that directory in question you actually formatted as something like a fat32 partition which doesn't support permissions...

---

### Post by mojoman on 2007-09-23
Well, all of the shared files are located on my /home partition but I haven't mucked around with fstab. Here's how it looks:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=595cc4b6-0140-4eb6-a5ae-f84cbb7abc93 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=2C708F07708ED6CC /mnt/windowsdisk     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=608a3d88-79ce-4aa3-857c-0bfaf881b29a /home     ext3    defaults        0       2
# /dev/sda3
UUID=b7a5c527-2320-40be-bf5e-b7e6a650f246 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

As you can see, only the windows partiton have a specific umask set (though I don't know why).

Here's the output of ls -l
```
drwxrws---  17 root     private   4096 2007-09-22 23:28 download
drwx------   2 root     root     16384 2006-09-18 20:32 lost+found
drwxr-x--- 110 mojoman  mojoman  16384 2007-09-23 09:43 mojoman
drwxrws---  15 root     private  12288 2007-09-22 23:17 movies
drwxrws---  29 root     private   4096 2007-09-22 15:11 music
drwxr-x---  24 promilla promilla  4096 2007-09-23 09:43 promilla
drwxr-xr-x   2 root     root      4096 2007-09-22 20:54 Recycled
drwxrws---   2 root     private   4096 2007-09-18 12:55 temporary
drwxrws---   3 root     private   4096 2007-09-22 13:11 torrents
drwxrws---   4 root     private   4096 2007-09-22 16:06 upload
```

Is this any help at all?
/mojoman

---

