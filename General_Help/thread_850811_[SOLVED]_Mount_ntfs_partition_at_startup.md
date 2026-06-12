---
title: "[SOLVED] Mount ntfs partition at startup"
date: 2008-07-06
forum: General Help
---

### Post by owoaux on 2008-07-06
*Hello, everyone! This is my first thread at 'Ubuntu Forums' I want to apologize for the not so good english of mine but I hope you'll understand me xD. Sorry if the thread is not in the right category though I checked carefully.*

What I want is to mount one of my ntfs partitions at every startup of Ubuntu. The partition I want to mount is my 'Music' partition ^^ 
Thanks, in advance,
Philip

---

### Post by orlox on 2008-07-06
You can use the diskmounter script to do that.

[diskmounter]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by tjwoosta on 2008-07-06
first off, find out what is the name of the partition where it is located

```
sudo fdisk -l
``` (for example it will be something like /dev/sda2)

then find out if you already have a mountpoint created by looking in the /media directory (it should say something like xxGB Media)

if not make a mountpoint named Music (or whatever) like this
```
sudo mkdir /media/Music
```

then edit your /etc/fstab to point toward the parition like this
```
gksudo gedit /etc/fstab
```

add this line to the very bottom (**where xxxx is whatever partition you found with fdisk -l and /media/whatever is whatever directory you made**)

/dev/xxxx          /media/whatever  ntfs defaults,umask=007,gid=46 0 1 0

(try to line it up with the existing entry)

then mount
```
sudo mount /dev/xxxx /media/whatever
```

and restart


just for future reference, questions like this one that are fairly common will usually get answered alot quicker when you post them in the "absolute beginner forum"

---

### Post by rraj.be on 2008-07-06
All the above stated ways will work.

But, The simplest way to do this is to use 

NTFS-Configuration tool


First unmount all your NTFS partitions

Go to ```
Application's-->System Tools-->NTFS configuration tool's.
```

If it's not there
you have to install it.

to install type this in terminal

```
sudo apt-get install ntfs-config
```

```
select all required partitions and select the mount point's.

Click Apply

It will give you a pop up window.

In that select Enable read write acces to internal devices.

Click apply.

Reboot.
```

That's IT.

---

### Post by jw5801 on 2008-07-06
> **tjwoosta said:**
> first off, find out what is the name of the partition where it is located

```
sudo fdisk -l
``` (for example it will be something like /dev/sda2)

then find out if you already have a mountpoint created by looking in the /media directory (it should say something like xxGB Media)

if not make a mountpoint named Music (or whatever) like this
```
sudo mkdir /media/Music
```

then edit your /etc/fstab to point toward the parition like this
```
gksudo gedit /etc/fstab
```

add this line to the very bottom (**where xxxx is whatever partition you found with fdisk -l and /media/whatever is whatever directory you made**)

/dev/xxxx          /media/whatever  ntfs defaults,umask=007,gid=46 0 1 0

(try to line it up with the existing entry)

then mount
```
sudo mount /dev/xxxx /media/whatever
```

and restart


just for future reference, questions like this one that are fairly common will usually get answered alot quicker when you post them in the "absolute beginner forum"

There's a random 1 in the middle of that fstab line. You don't really want that there! The line should look like:
```
/dev/xxxx */mount/point* ntfs defaults,umask=007,gid=46 0 0
```

---

### Post by owoaux on 2008-07-06
Thank you guys, your help rly solved my problem =)

---

### Post by ovidiu_b13 on 2011-05-01
Can you please explain the line? I understand it partialy, but ```
ntfs defaults, unmask=007, gid=46 0 0
```

I don't know what it means. I guess unmask=007 is to grant read-write access?

---

