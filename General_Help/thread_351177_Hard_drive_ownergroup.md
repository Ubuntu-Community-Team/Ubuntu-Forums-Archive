---
title: "Hard drive /owner/group"
date: 2007-02-01
forum: General Help
---

### Post by ronbrooks on 2007-02-01
I have a second hard drive in this computer and every time I put a file on the drive it gets the same owner (root) and the same group (plugdev).  I would like to change the owner to me so I can change the group settings.  

Each time I use sudo chown (me) /media/hdb6 I get this operation not permitted. 

How can I change the partition so that I own it.

---

### Post by taurus on 2007-02-01
What filesystem is /dev/hdb6, anyway?  Chown won't work if it's ntfs or vfat though.

---

### Post by ronbrooks on 2007-02-01
This is the output of fdisk for that partiion

/dev/hdb6            2433        3649     9775521    b  W95 FAT32

---

### Post by bodhi.zazen on 2007-02-01
You can do this by modifying fstab ...

Change your fstab entry to:

> /dev/hdb6 <mount_point> vfat auto,users,o=<your_user_name>,g=users 0 0

See here for more information: [How to fstab](http://www.ubuntuforums.org/showthread.php?&t=283131)

---

### Post by ronbrooks on 2007-02-01
Ok here is how my fstab file looks for that patistion 

# /dev/hdb6
UUID=19EA-5882  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1

Is this the right change to make

# /dev/hdb6
UUID=19EA-5882  /media/hdb6     vfat    auto,users,0=ronbrooks,g=user 0       1
I am not sure what the [/code} is.

I just don't want to mess this up again that is why I am taking it one step at a time. 

again thanks for your help.

---

### Post by bodhi.zazen on 2007-02-01
> **ronbrooks said:**
> Ok here is how my fstab file looks for that patistion 

# /dev/hdb6
UUID=19EA-5882  /media/hdb6     vfat    defaults,utf8,umask=007,gid=46 0       1

Is this the right change to make

# /dev/hdb6
UUID=19EA-5882  /media/hdb6     vfat    auto,users,0=ronbrooks,g=user 0       1

That should be a small letter O and not the number 0.

Otherwise try this:> # /dev/hdb6
UUID=19EA-5882  /media/hdb6     vfat    auto,utf8,users,o=ronbrooks,g=user,umask=007 0       0


> I am not sure what the [/code} is.

Well, it is a typo, I fixed it ;)

> I just don't want to mess this up again that is why I am taking it one step at a time. 

again thanks for your help.

It is a good habit to back up sys files before you edit them.

Backup:```
sudo cp /etc/fstab /etc/fstab.bak
```

If you need to restore:```
sudo cp /etc/fstab.bak /etc/fstab
```

HTH

---

### Post by ronbrooks on 2007-02-02
Well I tried both changes and it didn't work. this is the changes i made to my fstab.

UUID=19EA-5882  /media/hdb6     vfat    auto,utf8,user,o=ronbrooks,g=user,unmask=007 0 0

This is what I got when I ran mount -a

ronbrooks@prodigy:~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/19EA-5882,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

what do I need to change to make this work.

---

### Post by bodhi.zazen on 2007-02-02
First, it is UMASK not unmask (no n)

umask=007 not unmask

Second, 

You may need to use numbers instead of names for your owner and group options.

See here for a tutorial on how to identify your user ID and group ID:

[http://www.reallylinux.com/docs/usersubuntu.shtml](http://www.reallylinux.com/docs/usersubuntu.shtml)

Thus your fstab entry will look something like this (if you use numbers):
> UUID=19EA-5882 /media/hdb6 vfat auto,utf8,user,o=1000,g=100,umask=007 0 0

HTH

---

### Post by ronbrooks on 2007-02-02
First of all I want to thank you for your help.  

I made the changes here as you have suggested. 

UUID=19EA-5882  /media/hdb6     vfat    auto,utf8,user,o=ronbrooks,g=user,umask=007 0 0


ronbrooks@prodigy:~$ sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
mount: wrong fs type, bad option, bad superblock on /dev/disk/by-uuid/19EA-5882,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I was just wondering do I have to unmount the drive before I make the changes to the fstab file.  When I reboot my computer the drive dose not show up on the desktop so that means it will not mount.   When I use the undo command on the fstab  and restart it comes back.  I also tried to us my group number in place of my name and that did nothing. 

I don't know if this will help but I ran the dmesg | tail and this is what I got. 

ronbrooks@prodigy:~$ dmesg | tail
[17179616.456000] Bluetooth: RFCOMM TTY layer initialized
[17179616.456000] Bluetooth: RFCOMM ver 1.7
[17179616.624000] NET: Registered protocol family 10
[17179616.624000] lo: Disabled Privacy Extensions
[17179616.624000] IPv6 over IPv4 tunneling driver
[17179674.416000] FAT: Unrecognized mount option "o=ronbrooks" or missing value
[17179794.628000] PPP BSD Compression module registered
[17179794.740000] PPP Deflate Compression module registered
[17180223.832000] FAT: Unrecognized mount option "o=1000" or missing value
[17180564.140000] FAT: Unrecognized mount option "o=ronbrooks" or missing value

---

### Post by bodhi.zazen on 2007-02-02
Ack, me bad :redface:

Try uid= and gid=

Either uid=ronbrooks and gid=user
> UUID=19EA-5882 /media/hdb6 vfat auto,utf8,user,uid=ronbrooks,gid=user,umask=007 0 0

Or

uid=1000 gid=100
> UUID=19EA-5882 /media/hdb6 vfat auto,utf8,user,uid=1000,gid=100,umask=007 0 0


---

### Post by ronbrooks on 2007-02-02
Again thank you very much.

The second one worked and I now own the partition and user is the group name.  Now I am happy!    :) If a break it again I will try and put the piece back together again.  

Your help has been great and I have learn a lot form you. If I have any more trouble I will make another post.

---

### Post by Godan on 2007-04-08
Your query helped me too!  Thanks to all who gave input.  

I've got my USB FAT32 partition usable over the network.  

But!!!!  

Can something similar be done with an NTFS partition?

---

### Post by bodhi.zazen on 2007-04-08
> **Godan said:**
> Your query helped me too!  Thanks to all who gave input.  

I've got my USB FAT32 partition usable over the network.  

But!!!!  

Can something similar be done with an NTFS partition?

Yes, ntfs takes the same options as FAT32 EXCEPT for write access.

For read-write access try ntfs-config :

ntfs-config : [http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

