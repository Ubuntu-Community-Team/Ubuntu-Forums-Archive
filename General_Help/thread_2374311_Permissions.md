---
title: "Permissions"
date: 2017-10-14
forum: General Help
---

### Post by daniell59 on 2017-10-14
I just formatted my second hard drive to ext 4. I am having difficulty figuring out how to get permissions so that I can use it for storage.
Ubuntu 14.04 32

Thanks in advance

---

### Post by The Cog on 2017-10-14
Probably the easiest thing to do is to make the drive read/write by everybody. Assuming it is mounted at /mnt/storage(you didn't say), change the permissions to read/write by everybody with the command:
```
sudo chmod 777 /mnt/storage
```

---

### Post by oldfred on 2017-10-14
Generally 777 is not recommended. 

       #If you cannot read and write then change the permissions. Not for NTFS
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# 777 is read, write & execute by everyone
Seems like a better way as you have more control over what is executable. Isee post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369)
sudo chmod -R a+rwX,o-w /mnt/data
#is better than this:
sudo chmod -R 777  /mnt/data

Also may want this:
sudo chown -R $USER:$USER /mnt/data
#where $USER should be your login name
#or to see user
echo $USER 

I typically create mount point like /mnt/data
then mount partition and do chmod & chown of all data on drive (if it already has data)
Then add to fstab if internal drive, so auto mounted on reboot.

      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 


 Typical fstab entry For ext4, copy & paste into fstab but use your UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /mnt/data ext4 defaults,noatime 0 2

---

### Post by Dennis N on 2017-10-14
The file system on a new partition at first belongs to root (since root created it). You can change the owner to your user, which will give you all needed access permissions. 

If your user name is joe, and the partition mounts at /mnt/xxxx then

```
sudo chown -R joe:joe /mnt/xxxx
```

will give you ownership and all the necessary access permissions as well.

---

### Post by ajgreeny on 2017-10-14
I do what Dennis N says and simply use chown on the mountpoint rather than worry about specific permissions as my machine is single user.

If you have more than one user you may need to use permissions (chmod commands) to allow access by other users and groups.

---

### Post by daniell59 on 2017-10-14
I am having difficulty with this. I cannot even figure out how to change the mount point.
Mounted on /media/daniel/9a1bdfd7-a67c-4086-9585-7687419a32d2

---

### Post by deadflowr on 2017-10-14
> **daniell59 said:**
> I am having difficulty with this. I cannot even figure out how to change the mount point.
Mounted on /media/daniel/9a1bdfd7-a67c-4086-9585-7687419a32d2

Terminal wise should be
```
sudo umount /media/daniel/9a1bdfd7-a67c-4086-9585-7687419a32d2
```
File Manage wise, there should be a listing in a side panel (usually most file manager do this)
And the external devices that are mounted will show an eject like button, simply pressing the eject icon will unmount the device(or at most ask for a password to do the unmounting)

From there it should simply be about remounting it in the new locale.

---

### Post by daniell59 on 2017-10-14
> **deadflowr said:**
> Terminal wise should be
```
sudo umount /medai/daniel/9a1bdfd7-a67c-4086-9585-7687419a32d2
```
File Manage wise, there should be a listing in a side panel (usually most file manager do this)
And the external devices that are mounted will show an eject like button, simply pressing the eject icon will unmount the device(or at most ask for a password to do the unmounting)

From there it should simply be about remounting it in the new locale.

Thanks, I was not precise with my statement. I wanted to change the name of the mount point. Also, and mainly, I want to give permission so that I can use the hard drive. Please forgive me if I am making inane statements

---

### Post by deadflowr on 2017-10-14
Do you mean the rather long uuid string?

If so, then you can set a new label with
```
sudo tune2fs -L new-name-here /dev/sdXx
```
big X being the hard drive, little x being the partition number

---

### Post by daniell59 on 2017-10-14
> **deadflowr said:**
> Do you mean the rather long uuid string?

If so, then you can set a new label with
```
sudo tune2fs -L new-name-here /dev/sdXx
```
big X being the hard drive, little x being the partition number

I meant the path.

---

### Post by deadflowr on 2017-10-14
> **daniell59 said:**
> I meant the path.

My advice from before holds.
You need to unmount it first, then you can remount it in the new location, new path.
Most file managers have a hardcoded path setting to mount external drives in the /media directory, and that's typically non-negotiable.
So to reset using a different path you need to do so through the terminal.

---

### Post by daniell59 on 2017-10-14
I now have permission. I used the following sudo chmod ugo+wx-------

I wish that I knew what I did.

---

### Post by ajgreeny on 2017-10-15
From **man chmod** in terminal:-
> A  combination of the letters ugoa controls which users' access to the file will be changed: the user who owns
it (u), other users in the file's group (g), other users not in the file's group (o), or all  users  (a).   If
none  of  these  are  given,  the  effect  is as if (a) were given, but bits that are set in the umask are not
affected.

The letters rwxXst select file mode bits for the affected users: read (r), write (w), execute (or  search  for
directories)  (x),  execute/search  only if the file is a directory or already has execute permission for some
user (X), set user or group ID on execution (s), restricted deletion flag or sticky bit (t).  Instead  of  one
or  more of these letters, you can specify exactly one of the letters ugo: the permissions granted to the user
who owns the file (u), the permissions granted to other users who are members of the file's group (g), and the
permissions granted to users that are in neither of the two preceding categories (o).
so that command adds write and execute permissions, **+wx**, to the files for the user who owns them, group and others, **ugo**.

---

