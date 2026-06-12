---
title: "Mount share in FSTAB for NFS"
date: 2015-08-04
forum: General Help
---

### Post by AtomicPenguin on 2015-08-04
On my server I have an external USB drive (/dev/sdb2).  When plugged in this drive mounts as '/media/my_username/Movies'.

In my ext/export file I have '/export/movies  192.168.1.145(rw,no_root_squash,async,no_subtree_check,insecure)' which allows my networked media player to see the NFS share.

This is an NTFS drive.  What do I need to have in FSTAB to automount it properly?

According to the guide I would use something like.....

/media/my_username/Movies/Movies1    /export/movies   none    bind  0  0

but this isn't working.

When I first mounted the share NFS share with ' sudo mount --bind /media/my_username/Movies/Movies1 /export/movies' it was fine but after a reboot it fails to mount it via FSTAB.

---

### Post by papibe on 2015-08-04
Hi AtomicPenguin.

First get the UUID of the disk:
```
sudo blkid
```
You'll get a list of all your disks. Look for the one it is NTFS formated. For instance:
```
/dev/sdd1: LABEL="My Book" UUID="02D0852FD08529CC" TYPE="ntfs" 
```
Since you will be mounting it manually, you can decide where to mount it. Usually short paths work best for shared directories. Note that the directory and the path must exist before mounting anything on it.

This is an example:
```
sudo mkdir /nfs
sudo mkdir /nfs/movies
```
Now you can create an entry in your fstab:
```
sudo nano /etc/fstab
```
Go to the end of the file and add a line like this:
```
# WD My Book external 1TB USB drive
UUID="02D0852FD08529CC"  /nfs/movies  ntfs  noauto,uid=1000,gid=1000,umask=077  0  2
```
Use your UUID, and change the uid, and gid to other values if your user has other ids.

Hope it helps. Let us know how it goes.
Regards.

P.S.: you may want to read about certain problems and offered solutions for external USB hard drives on servers [here]("http://ubuntuforums.org/showthread.php?t=2286937&highlight=noauto+ntfs").

---

### Post by bab1 on 2015-08-04
> **AtomicPenguin said:**
> On my server I have an external USB drive (/dev/sdb2).  When plugged in this drive mounts as '/media/my_username/Movies'.

In my ext/export file I have '/export/movies  192.168.1.145(rw,no_root_squash,async,no_subtree_check,insecure)' which allows my networked media player to see the NFS share.

This is an NTFS drive.  What do I need to have in FSTAB to automount it properly?

According to the guide I would use something like.....

/media/my_username/Movies/Movies1    /export/movies   none    bind  0  0

but this isn't working.

When I first mounted the share NFS share with ' sudo mount --bind /media/my_username/Movies/Movies1 /export/movies' it was fine but after a reboot it fails to mount it via FSTAB.
There are 3 parts to this.  

Firest is how you mount the external drive to the computer that is the server.  This you seem to have done using the udev auto mount.  This is the only time when the drives formatting is important.  I'm quite sure that udev understood and mounted it with the proper formatting driver (ntfs-3g).  You can check it with this command```
mount
```.  Look down the list and see if you can see the disk mounted at '/media/my_username/Movies'.

Second is that you have to use mount -bind for NFS (not NTFS ) to relocate the drive to /exports.  I do something like this
```
# Mount bind the directory to the /exports file system
/srv/share/data/pictures /exports/pictures none bind 0 0

```...I assume here that NFS is working for you.  ;-)

Third is how you mount the NFS "exported" file system on the client.  I use something like this on my Ubuntu clients```
# Pictures
192.168.1.2:/exports/pictures /home/bab/Pictures    nfs   user,noauto,defaults    0       0

```

---

### Post by AtomicPenguin on 2015-08-05
> **papibe said:**
> Hi AtomicPenguin.

First get the UUID of the disk:
```
sudo blkid
```
You'll get a list of all your disks. Look for the one it is NTFS formated. For instance:
```
/dev/sdd1: LABEL="My Book" UUID="02D0852FD08529CC" TYPE="ntfs" 
```
Since you will be mounting it manually, you can decide where to mount it. Usually short paths work best for shared directories. Note that the directory and the path must exist before mounting anything on it.

This is an example:
```
sudo mkdir /nfs
sudo mkdir /nfs/movies
```
Now you can create an entry in your fstab:
```
sudo nano /etc/fstab
```
Go to the end of the file and add a line like this:
```
# WD My Book external 1TB USB drive
UUID="02D0852FD08529CC"  /nfs/movies  ntfs  noauto,uid=1000,gid=1000,umask=077  0  2
```
Use your UUID, and change the uid, and gid to other values if your user has other ids.

Hope it helps. Let us know how it goes.
Regards.

P.S.: you may want to read about certain problems and offered solutions for external USB hard drives on servers [here]("http://ubuntuforums.org/showthread.php?t=2286937&highlight=noauto+ntfs").

I actually don't want to mount it manually on each reboot.  How would I get around that?

---

### Post by AtomicPenguin on 2015-08-05
So if I put...

/media/jason/Movies /export/movies none bind 0 0

...in my /etc/fstab I end up not being able to browse the '/export/movies' folder.  It tells me permission denied.

I did a chown to the 'movies' folder to nobody:nogroup but I can't navigate to it.  Meanwhile it looks like udev auto mount mounted the drive still to /media/jason/Movies

---

### Post by bab1 on 2015-08-05
> **AtomicPenguin said:**
> So if I put...

/media/jason/Movies /export/movies none bind 0 0

...in my /etc/fstab I end up not being able to browse the '/export/movies' folder.  It tells me permission denied.

I did a chown to the 'movies' folder to nobody:nogroup but I can't navigate to it.  Meanwhile it looks like udev auto mount mounted the drive still to /media/jason/Movies
Are you referring to the *bind mount* on the server?  If so, I would say the syntax is correct.  Permissions are a different matter.  NFS uses user ID's to allow **remote **access.  All of my users have the same user ID on all hosts.  It doesn't matter what machine.  For example I am always user 1000.

You should be able to navigate (browse the file tree)  to the remotely mounted NFS export. I do it every day.  My advice is to control everything regarding the NFS exports.  You mount the external drive (via fstab) and you mount bind the section of the file system to the /exports directory in fstab also.  You have to manage the users assigned ID's (uid).

You should not try and automagically configure NFS.  FWIW, I mount my data partitions (drives) at /srv/share/<some_dir> and then *mount bind* that mounted partition to /exports/<some_dir> (where <some_dir> is your choice).  Look at my examples.

You can't rely on udev to mount the external drive the same way each time.  It can (does) change!

Your first step is to mount the external drive partition at some location outside of /media.  The preferred location for file servers is /srv, but it is not mandatory.  With NTFS partitions you need to set the permissions at mount time.  You can't change them afterwards.  How many network users are there?

---

### Post by AtomicPenguin on 2015-08-06
What I'm after is setting up this NFS share for my [WDTV Live]("http://www.wdc.com/en/products/products.aspx?id=1270").

I originally tested NFS shares with it by using my /home/jason/Videos directory and that went great.  No issues whatsoever.  So I can't help but think that NTFS is what's giving me all my grief at this point.

After realizing that my PC case had room for another drive inside of it I went ahead and pulled the drive out of the enclosure and it is now an internal drive - so it is directly connect via SATA and not USB.  I'm thinking this may reduce some of my complications but what do I know? :D

With it as an internal drive (still NTFS) I'm able to get it mounted but it insists on setting permissions on the /export/movies folder (where I'm mounting it to for NFS) to root:root and that's no good. A chown doesn't modify it either.

My plan at this point is to get my hands on another 3TB drive (on loan from a friend) to backup my data to and reformat the drive to ext3 or ext4.  Not sure which one is best to go with?

---

### Post by bab1 on 2015-08-06
> **AtomicPenguin said:**
> What I'm after is setting up this NFS share for my [WDTV Live]("http://www.wdc.com/en/products/products.aspx?id=1270").

I originally tested NFS shares with it by using my /home/jason/Videos directory and that went great.  No issues whatsoever.  So I can't help but think that NTFS is what's giving me all my grief at this point.

I'm sure you are right.  NTFS is less flexible than ext4.  The permissions and ownership have to be set at the time you mount the partition.  You can't change ownership or permissions after that.
> 

After realizing that my PC case had room for another drive inside of it I went ahead and pulled the drive out of the enclosure and it is now an internal drive - so it is directly connect via SATA and not USB.  I'm thinking this may reduce some of my complications but what do I know? :D

It does not matter whether the HDD is internal or external.  You can reformat the HDD partition to ext4 whether it is internal or external/USB or SATA.
> 

With it as an internal drive (still NTFS) I'm able to get it mounted but it insists on setting permissions on the /export/movies folder (where I'm mounting it to for NFS) to root:root and that's no good. A chown doesn't modify it either.
See my comments above.> 

My plan at this point is to get my hands on another 3TB drive (on loan from a friend) to backup my data to and reformat the drive to ext3 or ext4.  Not sure which one is best to go with?
I would use ext4.  You should always have a backup of your data whatever you do.

---

