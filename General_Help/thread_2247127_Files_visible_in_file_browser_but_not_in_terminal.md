---
title: "Files visible in file browser but not in terminal"
date: 2014-10-05
forum: General Help
---

### Post by ahkond on 2014-10-05
I recently upgraded to 14.04, and along with various other problems I won't go into, I have lost the ability to browse the contents of my external hard drives via the Terminal. 

I have two external hard drives. I can browse both their contents via the "Files" application, but when I open a Terminal and try to cd there or otherwise interact with them, I get different behavior. 

For one drive, it appears in my /media folder in Terminal (with green aura around the letters for some reason) and I can cd into the drive's folder, but if I type "ls" it reports that the folder is empty. Then I look at it in the Files app and I see all my stuff. 

For the other drive, it also appears in my "media" directory (no green aura this time), but if I try to cd into it I get straight up "permission denied" which I never got before. If I try to manage its permissions I get various errors along the lines of "user does not exist", even if I open Nautilus via sudo; Nautilus generally crashes at that point, and when it tries to report a problem, that crashes too. 

I have tried unmounting and remounting the drives but nothing changes. Presumably I need to change something else somewhere. Sorry if this has already been asked and answered; I tried to search for similar problems but there's nothing specific enough to search on. Thanks

---

### Post by Vaphell on 2014-10-05
relevant *ls -la* output would be nice

---

### Post by Vaphell on 2014-10-05
relevant *ls -la* and *mount *output would be nice and maybe relevant parts of /etc/fstab if there are any

---

### Post by ahkond on 2014-10-05
> **Vaphell said:**
> relevant *ls -la* and *mount *output would be nice and maybe relevant parts of /etc/fstab if there are any


ls -la says this: 
total 20
drwxr-xr-x   5 root root 4096 Aug 17 22:07 .
drwxr-xr-x  22 root root 4096 Sep 23 21:28 ..
drwxr-x---+  4 root root 4096 Oct  5 19:12 bill
drwxrwxrwx   2 root root 4096 Aug 17 16:08 My Book
drwx------   2 root root 4096 Aug 17 16:08 MyBook2

"bill" is my internal (main) drive. "My Book" is the one I can enter using "cd" but "ls" shows it as empty; "MyBook2" is the one I cannot enter with "cd" at all. 

Running mount gives this: 

/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=bill)
/dev/sdb1 on /media/bill/MyBook2 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdc1 on /media/bill/My Book type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)


I have no idea what parts of /etc/fstab would be relevant. Assuming it to be a directory I tried "cd /etc/fstab" and got this: 
bash: cd: /etc/fstab: Not a directory

---

### Post by Vaphell on 2014-10-05
MyBook2 lacks permissions and only direct owner (root) has access to it. 'group' and 'others' are denied. Read and execute are required to have access to dir contents.
What is the ls -la output for MyBook? Is there something special about the filenames in it?

---

### Post by septekin on 2014-10-06
For the "green aura around some letters" you may try sudo chmod xxx <name>. You may even try the same mode letters that are shown in the list!

To satisfy Vaphell, you may run gedit /etc/fstab and copy the contents of the text file that will appear.

For accessing the contents of some of your folders in the Terminal, I wonder if you are allowing for the "improved file structure" in 14.04 where the mounted folders and the home folder are no longer in their traditional places but under /media/ubuntu/ and /home/ubuntu/user?

Please do take my suggestions with a pinch of salt because I am not an expert, just hoping to share my experiences. Good luck.

---

### Post by ahkond on 2014-10-08
> **Vaphell said:**
> MyBook2 lacks permissions and only direct owner (root) has access to it. 'group' and 'others' are denied. Read and execute are required to have access to dir contents.
What is the ls -la output for MyBook? Is there something special about the filenames in it?

Sorry for not replying sooner. 

If I'm in /media and type ls -la, I get this: 
total 20
drwxr-xr-x   5 root root 4096 Aug 17 22:07 .
drwxr-xr-x  22 root root 4096 Sep 23 21:28 ..
drwxr-x---+  4 root root 4096 Oct  5 19:12 bill
drwxrwxrwx   2 root root 4096 Aug 17 16:08 My Book
drwx------   2 root root 4096 Aug 17 16:08 MyBook2

if I type ls -la "My Book", I get this: total 8
drwxrwxrwx 2 root root 4096 Aug 17 16:08 .
drwxr-xr-x 5 root root 4096 Aug 17 22:07 ..

If I cd into "My Book" and type "ls -la", I get the same. 

The above output omits all the actual contents of the folder that I can see in the Nautilus / Files UI. 

I know that the permissions on MyBook2 are missing, but I am unable to set them. Attempting to do so from Terminal yields errors, and attempting to do so from the Nautilus / Files UI causes it to crash. I managed to change some permissions on "My Book" and that's what got "My Book" into its weird state. 

There is nothing unusual about the filenames in either "My Book" or MyBook2; in fact MyBook2 is currently a clone of "My Book" as of a few weeks ago (I use a dopey backup script to copy a lot of stuff over). I have folders with names like "tunes" and "backups" and "playlists" and other simple stuff.

---

### Post by ahkond on 2014-10-08
> **septekin said:**
> For the "green aura around some letters" you may try sudo chmod xxx <name>. You may even try the same mode letters that are shown in the list!

To satisfy Vaphell, you may run gedit /etc/fstab and copy the contents of the text file that will appear.

For accessing the contents of some of your folders in the Terminal, I wonder if you are allowing for the "improved file structure" in 14.04 where the mounted folders and the home folder are no longer in their traditional places but under /media/ubuntu/ and /home/ubuntu/user?

Please do take my suggestions with a pinch of salt because I am not an expert, just hoping to share my experiences. Good luck.

Thanks; using gedit on /etc/fstab like you suggested gives me this: 

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=2989415a-6fb0-4a1c-9862-ec656b70f4e2 none            swap    sw              0       0

I had no idea about a file structure change and do not know whether I am expected to remount things in new locations, or how to do that.

---

### Post by ahkond on 2014-10-12
I've used chmod to change the permissions on my two external drives to match the permissions on my internal drive. I am still unable to cd into my external drives. 

ls -la now tells me this: 

drwxr-xr-x   5 root root 4096 Aug 17 22:07 .
drwxr-xr-x  22 root root 4096 Oct  9 20:33 ..
drwxr-x---+  4 root root 4096 Oct 12 10:31 bill
drwxr-x---   2 root root 4096 Aug 17 16:08 My Book
drwxr-x---   2 root root 4096 Aug 17 16:08 MyBook2

The only difference I see is that my internal drive has a "+" at the end of its ls -la output. Apparently this means that there is an access control list (ACL) of accounts/users that can *grant* additional permissions. Calling getfacl on these 3 produces the following: 

# file: bill
# owner: root
# group: root
user::rwx
user:bill:r-x
group::---
mask::r-x
other::---

# file: My Book
# owner: root
# group: root
user::rwx
group::r-x
other::---


# file: MyBook2
# owner: root
# group: root
user::rwx
group::r-x
other::---

Do I need to make the ACL on the external drives look like the ACL on the internal drive? Or is that beside the point, if it's only about listing who can *GRANT* permissions? Should I attempt to use setfacl to get the ACL stuff to match? Or am I wasting time? 

I'm still stuck, I still can't navigate into my external drives via "cd" in the Terminal. Help! 

Thanks

---

### Post by Dennis N on 2014-10-12
MyBook2 has an ext4 file system. I assume it is for your data? Why don't you just change the owner and group of that drive to your user name? That's what I do with my external data drive with an ext4 file system. Then you are the owner and get all the owner's permissions - read, write, and execute.

If your user name is bill,

```
sudo chown bill:bill /media/bill/MyBook2
```

---

### Post by ahkond on 2014-10-13
> **Dennis N said:**
> MyBook2 has an ext4 file system. I assume it is for your data? Why don't you just change the owner and group of that drive to your user name? That's what I do with my external data drive with an ext4 file system. Then you are the owner and get all the owner's permissions - read, write, and execute.

If your user name is bill,

```
sudo chown bill:bill /media/bill/MyBook2
```

Thanks, I tried that. It had no effect. I still cannot cd into MyBook2, and ls -la still lists root as the owner: 

bill@bill-desktop:/media$ sudo chown bill:bill /media/bill/MyBook2
[sudo] password for bill: 
bill@bill-desktop:/media$ cd MyBook2
bash: cd: MyBook2: Permission denied
bill@bill-desktop:/media$ ls -la
total 20
drwxr-xr-x   5 root root 4096 Aug 17 22:07 .
drwxr-xr-x  22 root root 4096 Oct  9 20:33 ..
drwxr-x---+  4 root root 4096 Oct 12 10:31 bill
drwxr-x---   2 root root 4096 Aug 17 16:08 My Book
drwxr-x---   2 root root 4096 Aug 17 16:08 MyBook2
bill@bill-desktop:/media$ 

It reported no error after the chown command but it seems to have accomplished nothing.

---

### Post by nerdtron on 2014-10-13
It's not /media/bill/MyBook2. It should be /media/MyBook2. Anyway,

Try it with recursive just to be sure on the inside folders.
```
sudo chown -R bill:bill /media/*
```

Or if you want to see everything why not give read access to everything. This could be the shotgun:
```
sudo chmod -R a+r /media/* 
```

---

### Post by nerdtron on 2014-10-13
>  It reported no error after the chown command but it seems to have accomplished nothing. 
Yah. It might have reported and error of wrong directory or it doesn't exist right?

---

### Post by ahkond on 2014-10-13
> **nerdtron said:**
> It's not /media/bill/MyBook2. It should be /media/MyBook2. Anyway,

Try it with recursive just to be sure on the inside folders.
```
sudo chown -R bill:bill /media/*
```

Or if you want to see everything why not give read access to everything. This could be the shotgun:
```
sudo chmod -R a+r /media/* 
```

That allows me to cd into MyBook2 but if I type "ls" I still see nothing. The files and folders are all still hidden from me in Terminal but not in the Folders/Nautilus UI.

---

### Post by nerdtron on 2014-10-13
Can you provide the out put of "ls -lah" when you are inside the MyBook2?

Also I think we are referring to a different mount point here. Can you provide a screenshot of Nautilus with the files you are seeing. Then Press Ctrl+L to see the location (path) of this folder.

---

### Post by Dennis N on 2014-10-13
From Post #11:

```
bill@bill-desktop:/media$ ls -la
total 20
drwxr-xr-x 5 root root 4096 Aug 17 22:07 .
drwxr-xr-x 22 root root 4096 Oct 9 20:33 ..
drwxr-x---+ 4 root root 4096 Oct 12 10:31 bill
drwxr-x--- 2 root root 4096 Aug 17 16:08 My Book
[COLOR="#FF0000"]drwxr-x--- 2 root root 4096 Aug 17 16:08 MyBook2[/COLOR]

```
implies there is a directory **/media/MyBook2**
post #4 mount command shows mount point of the drive at:  **/media/bill/MyBook2**

So, **/media/MyBook2** is not the external drive, just a folder of the same name that was created in /media. It is empty, so you don't see anything. The chown on **/media/bill/MyBook2** worked, you are just not looking at it here.

This is causing the confusion.

---

### Post by nerdtron on 2014-10-13
What's causing confusion (or my suspicion) is that the mount point of his drive is different from the folder we are looking.
Might as well confirm the mount point on the following commands:

```
lsblk
mount
```

---

### Post by Dennis N on 2014-10-13
> What's causing confusion (or my suspicion) is that the mount point of his drive is different from the folder we are looking.

See post #16 if you missed it.

---

### Post by nerdtron on 2014-10-13
If it is mounted on /media/bill/MyBook2, there are other folder that could cause confusion on his #11 post.
```

bill@bill-desktop:/media$ ls -la
total 20
drwxr-xr-x   5 root root 4096 Aug 17 22:07 .
drwxr-xr-x  22 root root 4096 Oct  9 20:33 ..
drwxr-x---+  4 root root 4096 Oct 12 10:31 bill
drwxr-x---   2 root root 4096 Aug 17 16:08 My Book
drwxr-x---   2 root root 4096 Aug 17 16:08 MyBook2
bill@bill-desktop:/media$ 
```

He could be looking into /media/MyBook2 which really contains nothing, while his files are on /media/bill/MyBook2.

---

### Post by Dennis N on 2014-10-13
> **nerdtron said:**
> 
He could be looking into /media/MyBook2 which really contains nothing, while his files are on /media/bill/MyBook2.

Yes, this is correct. Again, look back at Post #16 where I showed the evidence for this.

---

### Post by ahkond on 2014-10-13
Thank you both, this was the problem. If I cd to /media/**bill**/My Book/foo/bar/etc all my stuff is there and I can manipulate and rename files. Prior to the 14.04 upgrade I believe I did this by cd'ing to /**media/"My Book"**/foo/bar/whatever but apparently they have moved (my old scripts and crib sheets all use this path and worked fine prior to the upgrade). I had not noticed that new "My Book" and "MyBook2" folders had appeared in the path under /media/bill. 

This machine is old and I'm thinking of migrating to new hardware within the next few months, so I'm happy to leave the other empty folders where they are, as they seem basically harmless and I can work around the issue. So I think we're good for now. 

Thanks again

---

### Post by Dennis N on 2014-10-13
Yes, if you upgraded from 12.04, that would explain how this happened. In 12.04 the mount point would have been /media/device and we can surmise it was just left there in your filesystem. Beginning with 12.10 the mount point for external drives was changed by adding the extra directory to give /media/<user>/device

In the future, when you get a new external drive and format it ext4, immediately afterwards change the owner of the mount point folder to your user name. chown without the -R option is sufficient to do that. Any files or folders copied to or created on the drive will then be owned by you.

---

