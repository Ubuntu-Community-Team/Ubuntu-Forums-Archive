---
title: "[SOLVED] File Permissions?"
date: 2008-07-08
forum: General Help
---

### Post by nkobel003 on 2008-07-08
I am having difficulties with my external hard drive. I messed around with chown and chmod to try to make the owner myself, but only made it so I cannot mount the volume.

My goal is to edit mp3 tag files.
I can achieve the goal by setting the permissions of my external hard drive to include read and write files.
I do not know how to do this.

Right now, it is saying
> Cannot mount volume
You are not privileged to mount the volume 'WD500'.
I was able to mount it anyway via sudo mount but I also want to be able to have it mount automatically on startup.

Any suggestions?

---

### Post by crossedout on 2008-07-09
If I am understanding correctly, you have an external HD that is always connected and you would like to have it mounted at startup as well as have it rw for your <username>.  If that is the case, refer to the link provided below:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
The link is an introduction to fstab and will explain alot of what you are asking about.  Once you read it over, if you need help editing fstab or understanding some of the options, just ask and we can assist you further.

-Xout

---

### Post by nkobel003 on 2008-07-13
Hmm, I've been playing around with the fstab before your post, but it did help me a lot, thanks. Still, though, I cannot even mount with my username. Here is what my fstab looks like:
```

/dev/sdb2 	/media/WD500 	ntfs-3g	 auto,users,uid=1000,rw,suid,dev,exec,async	0 	0

```

Any ideas? BTW, you were correct on what it is and what I want it to be (Ext. HD with rw for my username).

---

### Post by tech0007 on 2008-07-13
Either

1. Install ntfs-config.  'sudo apt-get install ntfs-config' then configure it to enable write permission on internal device. Or.

2. Add this line to /etc/fstab

/dev/sdb2 /media/WD500 ntfs-3g defaults,locale=en_US.utf8 0  0

---

### Post by nkobel003 on 2008-07-13
> Either

1. Install ntfs-config. 'sudo apt-get install ntfs-config' then configure it to enable write permission on internal device. Or.

2. Add this line to /etc/fstab

/dev/sdb2 /media/WD500 ntfs-3g defaults,locale=en_US.utf8 0 0 
That didn't work at all... Any other suggestions, perhaps with chown or chmod or changing the fstab or mounting options?

---

### Post by tech0007 on 2008-07-13
You have an ntfs filesystem on your ext WD500 right? chown,chmod won't work on files/folders inside ntfs filesystems. They're all owned by root.

Did you try my suggestion? It didn't mount on boot?

---

### Post by coffeecat on 2008-07-13
**nkobel003**, I notice you had UID=1000 in your fstab mount options. I'm not quite clear whether this is still so. If you are the first created user on your system you should have a UID of 1000, but to be sure go to System > Administration > Users and Groups and check what your UID is. If it's different that might be half your problem.

However - I'm posting from Ubuntu on a system where my second internal drive has one large partition (sdb1) formatted NTFS. My fstab line for that partition couldn't be simpler, viz:

```
/dev/sdb1    /media/sdb1    ntfs-3g    defaults    0    0
```I have no trouble reading/writing/accessing files on that partition. I realise yours is an external drive, but I wouldn't have thought that would make any difference so long as it is switched on when you boot up. Why not try simply 'defaults' and see what happens?

---

### Post by nkobel003 on 2008-07-13
> You have an ntfs filesystem on your ext WD500 right? chown,chmod won't work on files/folders inside ntfs filesystems. They're all owned by root.

Did you try my suggestion? It didn't mount on boot? 
It did not mount on boot. Strange... And I think, then, since all files/folders are owned by root, that mp3 id3 tag editing may be impossible.

> I have no trouble reading/writing/accessing files on that partition. I realise yours is an external drive, but I wouldn't have thought that would make any difference so long as it is switched on when you boot up. Why not try simply 'defaults' and see what happens?

Defaults does nothing and my user id is indeed 1000.

When I mount, I get two errors:
```
Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```
and
```
Cannot mount volume
Unable to mount the volume 'WD500'.
Details
Unprivileged user can not mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuild NTFS-3g with integrated FUSE support and make it setuid root. Please see more information at [http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
```

I visited the website but that didn't really help me.

---

### Post by nkobel003 on 2008-07-15
bump

---

### Post by bodhi.zazen on 2008-07-15
adapted from the wiki page :

first unmount the partition :

```
sudo umount /dev/sdb1
```put this in fstab :

```
/dev/sdb1  /media/sdb1  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8   0  0
```mount :

```
mount /media/sdb1
```

---

### Post by nkobel003 on 2008-07-15
> adapted from the wiki page :

first unmount the partition : ...

I tried this and still, I cannot edit the mp3 tag files :(

---

### Post by bodhi.zazen on 2008-07-15
With the partition mounted, can you show us the output of :

```
ls -l /media | grep sdb1
```

---

### Post by nkobel003 on 2008-07-18
This did not work either :(

---

### Post by nkobel003 on 2008-07-18
I apologize for the mistake of a post above, but here is the output:

```
mannequin@NAMELESS:~$ ls -l /media | grep WD500
drwxr-x--- 1 mannequin users 4096 2008-07-16 16:22 WD500
```

---

### Post by kzm. on 2008-07-18
Please type ```
$ id
```
should return something like:
```
uid=1002(xxx) gid=1004(xxx) groups=4(xxx),...
```. is your 'uid' "mannequin"? and is "users" listed under 'groups'?

---

### Post by bodhi.zazen on 2008-07-18
From what you posted it appears permissions are correct.

Can you post the permissions of the file you are trying to edit ?

ls -l /media/WD500/

---

### Post by nkobel003 on 2008-07-19
> **kzm. said:**
> Please type ```
$ id
```
should return something like:
```
uid=1002(xxx) gid=1004(xxx) groups=4(xxx),...
```. is your 'uid' "mannequin"? and is "users" listed under 'groups'?

My UID is mannequin and 'groups' lists 'users'.

---

### Post by nkobel003 on 2008-07-19
> **bodhi.zazen said:**
> From what you posted it appears permissions are correct.

Can you post the permissions of the file you are trying to edit ?

ls -l /media/WD500/

Here is the output: ```
mannequin@NAMELESS:~$ ls -l '/media/WD500/Media/Music/AFI/Sing the Sorrow/11 The Leaving Song.mp3' 
-rw-r----- 2 mannequin users 3944524 2008-04-10 03:23 /media/WD500/Media/Music/AFI/Sing the Sorrow/11 The Leaving Song.mp3
```

---

### Post by bodhi.zazen on 2008-07-19
Well, your permissions look "OK"

your uid is 1002, rather then 1000 so you might need to change your line in fstab

Unmount the partition, then edit fstab, then remount the partition.

```
/dev/sdb1  /media/sdb1  ntfs-3g  auto,users,**uid=1002**,gid=100,dmask=027,fmask=137,utf8   0  0
```

---

### Post by nkobel003 on 2008-07-19
bodhi.zazen, how do you know my uid is 1002? either way, i tried what you said, and still i cannot edit the mp3 tags. (I think kzm was just using 1002 as an example)

---

### Post by bodhi.zazen on 2008-07-19
oic, looks like I mis read the postings then ...

It does not look like permissions are the issue here ...

Can you copy the file to ~ and try editing it from there ?
Can you copy a new file to the partition ?
Can you edit a different file in the partition ?

---

### Post by llebegue on 2008-07-19
Just some simple guess here ... is it a space caracter that I can see in the file name ?
If you used some command line tool for editing tags that would make e difference.

---

### Post by nkobel003 on 2008-07-19
> **bodhi.zazen said:**
> oic, looks like I mis read the postings then ...

It does not look like permissions are the issue here ...

Can you copy the file to ~ and try editing it from there ?
Can you copy a new file to the partition ?
Can you edit a different file in the partition ?

I can copy the files and edit them in a different location.
I can copy files to another partition.
As long as I added the files after I installed 8.04, I can edit other files, otherwise files on the drive *before* the 8.04 installation are also un-editable.

---

### Post by nkobel003 on 2008-07-19
> **llebegue said:**
> Just some simple guess here ... is it a space caracter that I can see in the file name ?
If you used some command line tool for editing tags that would make e difference.

It is not the spaced character, ' ' because I can edit other files with spaces (see above). BTW, I'm using EasyTag, but ExFacto, another tag editor gives me a similar error.

---

### Post by nkobel003 on 2008-07-20
I copied most of my music to another external hard drive, deleted it from WD500, then copied it back, and I can edit those tags with no problem. How do I change the rest of the existing files, though? I feel like it should be a simple command...

---

### Post by nkobel003 on 2008-07-24
bump

---

### Post by nkobel003 on 2008-07-28
no one has an answer yet?

---

### Post by nkobel003 on 2008-08-07
I guess the answer is to copy all of your data to an external hard drive, and then copy it back.

---

