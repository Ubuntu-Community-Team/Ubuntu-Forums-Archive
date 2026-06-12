---
title: "Backup utility"
date: 2008-07-06
forum: General Help
---

### Post by stair314 on 2008-07-06
Can anyone recommend a good backup utility? I'm thinking of something I can use to periodically copy my system to an external hard drive in a fairly automated way. Ideally I'd like to be able to reinstall a working system just from the backup, rather than having to install from scratch again.

---

### Post by rraj.be on 2008-07-06
You can use partimage.

[BUT ITS NOT AN AUTOMATIC PROCESS].

This has several capabilities like cloning entire partition Etc.

As you wanted, you can clone a partition of your installation and it can be stored   to a removable media or a disk so that you can just restore for installation.

The great thing about partimage is it just back's up your used space in a partition.

to install partimage type this in terminal
```

sudo apt-get install partimage
```

for further details go here.

```
[http://www.psychocats.net/ubuntu/partimage]("http://www.psychocats.net/ubuntu/partimage")
```

---

### Post by p_quarles on 2008-07-06
There are actually several different things you could mean by restoring "a working system" from your backup. The previous poster took you to mean making a complete image of your hard drive, which could then be re-imaged back onto the drive at any point, thus avoiding any kind of installation dialogue or software installation. 

That kind of backup is 1) time-consuming, and 2) difficult to automate, since it requires that the partitions of which you want to make images are not mounted.

Much easier to automate -- but less automated if/when you reinstall -- is to backup your various filesystems using an application based on rsync (grsync and flyback are the ones I can think of). These will not copy things like the partition table or the MBR, so you would first need to reinstall the OS before restoring these backups.

---

### Post by clsgis on 2008-07-06
> **stair314 said:**
> Can anyone recommend a good backup utility? I'm thinking of something I can use to periodically copy my system to an external hard drive in a fairly automated way. Ideally I'd like to be able to reinstall a working system just from the backup, rather than having to install from scratch again.

rraj.be suggested Partimage.  It's pretty tricky, snapshotting the raw partition but skipping the free (unused) blocks in the file system.

I'd suggest a shell script that mounts the external drive and calls GNU cp(1) a few times.  I have copied entire Ubuntu installations with, roughly,

```
  sudo su -
  mkfs.ext2 -J /dev/sdb1
  mkdir /tmp/target
  mount /dev/sdb1 /tmp/target
  d /tmp/target
  cp -a /bin /boot /dev /etc /home /initrd /lib /media /mnt \
             /net /opt /root /sbin /usr /var /vmlinuz .
  mkdir cdrom cdrom1 floppy loop proc sys tmp
  chmod 2777 tmp
  umount /tmp/target
  exit 
```

But you don't want to do this any old time.  There are "sockets files" in /var/run
 and /tmp.  Database files are in flux.  Logs are being written.  Files are doing stuff and you want everything to stop and remove its temp files.

  ```
sudo telinit 1
```

Do that and nothing will be running but your shell.  ```
telinit 5
``` will get you back your display manager.  Or do the copy operation from a live CD.  When you're done copying, boot the new drive from the install CD, and reinstall GRUB.

---

### Post by cariboo on 2008-07-06
Another backup utility is **sbackup**, it is very easy to setup. It does a full backup first and then only backups files that have been changed. You can set the interval on when it does a full backup and how often it just backs up changed files. Sbackup is in the repositories and you can use synaptic or Add/Remove Programs to install it.

Jim

---

### Post by ghostdog74 on 2008-07-06
your system will already have come with some. eg tar , cpio.

---

