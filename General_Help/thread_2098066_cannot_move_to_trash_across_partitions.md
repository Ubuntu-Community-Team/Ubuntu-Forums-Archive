---
title: "cannot move to trash across partitions"
date: 2012-12-25
forum: General Help
---

### Post by jopeto on 2012-12-25
I am using Ubuntu 12.10 with Unity. My system is installed on an ext4 partition. However, since I am dual-booting with other flavors of Linux, I have all my personal files stored onto an ext3 partition (called /dev/sda6), which I am mounting at boot-up using this line in /etc/fstab:

```
/dev/sda6       /media/home     ext3    noatime                 0       2
```

I have also created a symlink in the home directory of my ext4 partition so that all my files appear there. However when I try to delete a file in my ext3 directory, I get a message that the file cannot be moved to trash, but can only be deleted permanently.

I searched online and it appears that the problem is that there is no .Trash-1000 folder in my ext3 partition ([http://askubuntu.com/questions/69517/how-do-i-use-gnome-trash-for-files-in-different-partition](http://askubuntu.com/questions/69517/how-do-i-use-gnome-trash-for-files-in-different-partition)). However according to some information that I found, even if such a folder is created, then the files it contains will not appear in the trash bin of my ext4 partition. Apparently this has to do with the files not having to be moved across partitions upon deletion ([https://lists.ubuntu.com/archives/ubuntu-users/2005-December/060561.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-December/060561.html)).

So my question is the following:

Is it possible to have a set-up in which files from both the ext4 partition and the ext3 partition can be moved to the same trash folder on the ext4 partition so that they appear in the trash icon on the unity desktop or is that not currently possible?

---

### Post by jopeto on 2012-12-27
bump

---

### Post by rnerwein on 2012-12-27
> **jopeto said:**
> I am using Ubuntu 12.10 with Unity. My system is installed on an ext4 partition. However, since I am dual-booting with other flavors of Linux, I have all my personal files stored onto an ext3 partition (called /dev/sda6), which I am mounting at boot-up using this line in /etc/fstab:

```
/dev/sda6       /media/home     ext3    noatime                 0       2
```I have also created a symlink in the home directory of my ext4 partition so that all my files appear there. However when I try to delete a file in my ext3 directory, I get a message that the file cannot be moved to trash, but can only be deleted permanently.

I searched online and it appears that the problem is that there is no .Trash-1000 folder in my ext3 partition ([http://askubuntu.com/questions/69517/how-do-i-use-gnome-trash-for-files-in-different-partition](http://askubuntu.com/questions/69517/how-do-i-use-gnome-trash-for-files-in-different-partition)). However according to some information that I found, even if such a folder is created, then the files it contains will not appear in the trash bin of my ext4 partition. Apparently this has to do with the files not having to be moved across partitions upon deletion ([https://lists.ubuntu.com/archives/ubuntu-users/2005-December/060561.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-December/060561.html)).

So my question is the following:

Is it possible to have a set-up in which files from both the ext4 partition and the ext3 partition can be moved to the same trash folder on the ext4 partition so that they appear in the trash icon on the unity desktop or is that not currently possible?
hi
first i presume it's your mount option - noatime. no it isn't.
on my box i got the same message - why ?
looks like a bug. i'll will analyse it a little bit more to be sure.
here the strace of nautilus whit recomended calls.
lstat("/apache/lcmd/bla", {st_mode=S_IFREG|0664, st_size=5, ...}) = 0    ===> this is ok
lstat("/apache/lcmd/bla",  <unfinished ...>  ==> this is the second try of nautilus
but every other socket (i think it's a socket) calls fails
5115  poll([{fd=3, events=POLLIN}, {fd=6, events=POLLIN}, {fd=11, events=POLLIN}, {fd=10, events=POLLIN}, {fd=13, events=0}, {fd=9, events=POLLIN}, {fd=8, events=POLLIN}, {fd=20, events=POLLIN}, {fd=12, events=POLLIN}], 9, 500 <unfinished ...>
13527 <... futex resumed> )             = -1 ETIMEDOUT (Connection timed out)

5115  <... poll resumed> )
lstat("/apache/.Trash-1000",  <unfinished ...>
lstat("/apache/lcmd",  <unfinished ...>
.....
.....

sorry can't help you - but a nice problem.
cheers

---

### Post by jopeto on 2012-12-28
Thanks for your reply and your effort!

---

### Post by audiomick on 2012-12-28
> **jopeto said:**
> 
Is it possible to have a set-up in which files from both the ext4 partition and the ext3 partition can be moved to the same trash folder on the ext4 partition so that they appear in the trash icon on the unity desktop or is that not currently possible?

My guess is that this would not be possible. I think it contradicts the way the Linux file systems deal with deleted items.

I might add that I have seen this behaviour. I think it shows up on samba shares, and maybe on partitions that I have accessed but are not automounted. I am not too sure because it has never bothered me. When I delete something, I want it gone, if that message does disturb me in that particular instance, I think twice about deleting.

---

### Post by coffeecat on 2012-12-28
@jopeto, I've been doing some experimenting and it's almost certain that your problem is that the ext3 filesystem on /dev/sda6 is owned by root. The .Trash-1000 folder would be created in the root of the filesystem, but since the filesystem is owned by root (two meanings of the word root here) and .Trash-1000 would be is owned by you, it can't be created and you get the "cannot be moved to trash" message. You need to change ownership of the filesystem to yourself. Fortunately, this is easily done. If you run the chown command (and/or chmod) on the mountpoint of a mounted ext2/3/4 filesystem, you change the ownership of the filesystem itself, and not the mountpoint.

Assuming your /dev/sda6 is mounted on /media/home, then simply:

```
sudo chown yourusername: /media/home
```

Important:
[list][*]Substitute your account name for "yourusername".
[*]Don't forget the trailing colon after yourusername - that ensures ownership by your default group.
[*]Do **NOT** use the -R recursive flag. You want to chown only the filesystem, not all the hierarchy of contained folders and files.[/list]

If you are the only user of this partition, then this will be enough. If you have other users with other accounts accessing the partition, you would need to run a chmod command. Post back if you need this too.

---

### Post by audiomick on 2012-12-28
Hi Coffeecat. That sounds really logical. Thanks for that.

But that wont answer this, will it?

> **jopeto said:**
> 
Is it possible to have a set-up in which files from both the ext4 partition and the ext3 partition can be moved to the same trash folder on the ext4 partition so that they appear in the trash icon on the unity desktop or is that not currently possible?

As far as I can tell, that wont be possible because of the way the trash mechanism works, will it? Or am I quite mistaken there?

---

### Post by coffeecat on 2012-12-28
> **audiomick said:**
> 
As far as I can tell, that wont be possible because of the way the trash mechanism works, will it? Or am I quite mistaken there?

The OP is really asking two things:

> Is it possible to have a set-up in which files from both the ext4 partition and the ext3 partition can be moved to the same trash folder on the ext4 partition 

No, that's not possible - deleted files don't move across partitions. But...

> so that they appear in the trash icon on the unity desktop 

This is exactly how things are designed to work if you get the ownership/permissions right, which is why I am confident that a simple chown will fix things for the OP. The .Trash-1000 folder is created in the mounted partition, but if a file is moved there by a simple delete, the trash icon in the Unity launcher shows scrunched up paper. Empty the trash in the Unity launcher, and the files in .Trash-1000 get deleted properly. Or, more strictly, the files for deletion are in .Trash-1000/files/ .

This is exactly what happens with automounted USB drives. Delete a file on the USB drive and it gets moved to .Trash-1000 in the mounted filesystem, but the trash icon in the Unity launcher shows that something is in the trash.  

On my system, I have three mounted data partitions for personal files. In my case they are formatted ext4 rather than ext3, but that doesn't make any difference, and this is what I see. By chowning the three filesystems when I first set up the system, I avoided this issue.

---

### Post by rnerwein on 2012-12-28
> **audiomick said:**
> Hi Coffeecat. That sounds really logical. Thanks for that.

But that wont answer this, will it?



As far as I can tell, that wont be possible because of the way the trash mechanism works, will it? Or am I quite mistaken there?
hi
i know thats stuff of the underlaying permisions of the mount point ( i know it from System V but think it's not in Linux).
==> ls -ld /apache ===> drwxrwxrwx 19 root root 4096 Dez 26 19:09 /apache
and all the dirs and files in .local and .Trash-1000 are owned by me.
(the permissions are altered back !   :-)    )
it don't work. that don't hassle me because i now it now but i am just interested why.
cheers

---

### Post by audiomick on 2012-12-28
Ok, thanks very much for the explanation. :popcorn:

---

