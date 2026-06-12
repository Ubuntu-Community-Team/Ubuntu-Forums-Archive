---
title: "help understanding backup to ext4 partitioned HDD"
date: 2017-05-22
forum: General Help
---

### Post by ishmael3 on 2017-05-22
Can someone help me understand the permission/ownership implications of doing backups to an ext4-formatted external HDD?
 
 I have tried to do my homework, but help pages such as [[COLOR=#bc0d03]https://help.ubuntu.com/community/BackupYourSystem[/COLOR]]("https://help.ubuntu.com/community/BackupYourSystem") and [[COLOR=#bc0d03]https://help.ubuntu.com/community/DriveImaging[/COLOR]]("https://help.ubuntu.com/community/DriveImaging") 
make no mention of formatting. It was only after reading posts by experienced Linux users that I thought I should use ext4, but then ran into the problem of not being able to access the drive from regular user accounts That is, the ext4 partition is only accessible from the admin account.  

 My aim is to make three sorts of backups:
 1) disk image using clonezilla (or deja-dup via Ubuntu live ISO),
 2) Home Directory backups from each user account, using deja-dup,
 3) copies of individual files from user accounts.
 
 I'd like to NOT consider NTFS formatting as an option for the time being.  
 
 I am concerned about ease of procedure, that is, keeping it easy for any user to make backup files whenever desired.
 
 I'm also concerned about accidentally creating unusual directory/owner relationships that might cause system instability now, or that might not restore properly if it becomes necessary to restore backups later on.  
 
 Thanks for thoughts, advice, education!
 
 Computer is single-OS Ubuntu 16.04.  
 Backup HDD is 2-TB Seagate Expansion.

---

### Post by Bashing-om on 2017-05-22
ishmael3' Hi !

Look, only you can decide on ownership and the levels of access (permissions) you want to set on your system 
Let's start here  with these tutorials.

fstab tutorial: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Here we "assume" you want to auto mount "some" partitions ; that is the function of the /etc/fstab file .

Next you need to set the access rights to these file systems that you have mounted . - only you can say what it is that you want ; what will work for your particular use case .

see:
```

man chown
man chmod

```

And, when you are ready - we can continue this discussion IF you still have issues setting the system up to your satisfaction.

[INDENT][INDENT]it will be
[INDENT][INDENT][INDENT]what it will be
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2017-05-22
As part of my install script, I create a mount point and give myself ownership & permissions

sudo mkdir /mnt/backup
sudo chown $USER:$USER /mnt/backup
sudo chmod a+rwX /mnt/backup
Note that this is more like /home settings, not system.
I typically run with -R or recursion so I own all files & folders as I only backup my data, not system. 
But if system files you want to leave root, and many other system owners as the owner.

As part of my rsync backup script I make sure it is mounted ( I have some logic checking if already mounted)
I have in past not mounted it, and it created a new folder in / and filled my / which is not large.
My backup partition is sdb4.

my_mount="/mnt/backup"
sudo  mount -t ext4 /dev/sdb4 $my_mount
or
sudo  mount -t ext4 /dev/sdb4 /mnt/backup

---

### Post by SeijiSensei on 2017-05-22
If you back up the /home directory with "rsync -a" it will preserve the ownerships of the various directories.  So, for instance, running
```

cd /
sudo rsync -a home /path/to/backup/

```
will create an image of the home directories as /path/to/backup/home.  If /path/to/backup has at least 755 privileges at all levels, user janice should be able to access /path/to/backup/home/janice without sudo privileges.

---

### Post by ishmael3 on 2017-05-22
Thanks all for the responses.
 
 Bashing-om, those look like useful tutorials and it will take me a while to digest the new info. I am working on it.   
 
 oldfred, sorry, I don't understand why I would want to make a directory in /mnt rather than in /media/<user>. I had thought my task was going to be to create mount points for each user within media (like: /media/<user01>/<HDD_ID>, /media/<user02>/<HDD_ID>, etc.) and then set permissions for each of those directories.  That idea may be totally wrong.
 
 I also don't understand, if I DO create a mount point that is someplace besides /media (such as in /mnt), how I would keep any device that is plugged into the computer from first automatically mounting at /media/<current_user>/<device> instead .
 
 I think I could use a tutorial on the basics of how devices  are mounted and unmounted if anyone knows of one.  
 
 Thanks for patience and help!

---

### Post by oldfred on 2017-05-22
If you use Naulitus or file browser you get an auto mount with default parameters.
If a removable disk that probably is preferred.
And that would be by your label or UUID at /media/$USER/label
I do prefer to label all partitions and particularly any I do not normally mount with fstab.

But even my flash drives, I have manually mounted to use them. Often easier just to use the automount or manually mount to the standard auto mount location.
Manually mounting also lets you set your own parameters.

Mounts in /media will show in Nautilus left panel, and you must eject or unmount if removable using Nautilus.
I often do not want mount in Nautilus to avoid conflicts, so then use /mnt. But also have to manually unmount with umount command.

 Set Labels for external devices gparted, Disk Utility or command line
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
[http://askubuntu.com/questions/147319/how-can-i-give-other-drives-and-partitions-short-meaningful-names-in-nautilus](http://askubuntu.com/questions/147319/how-can-i-give-other-drives-and-partitions-short-meaningful-names-in-nautilus)

---

### Post by ishmael3 on 2017-05-23
Those are useful links and I've learned some things about mounting -- auto vs manual -- that I didn't know.  
 
 For other relative newbies, such as myself, here's an especially coherent discussion of mounting usb devices that I ran across:
[[COLOR=#bc0d03]https://askubuntu.com/questions/285539/detect-and-mount-devices[/COLOR]]("https://askubuntu.com/questions/285539/detect-and-mount-devices")

 Thanks, oldfred, for taking the time to help.

 And thanks, Bashing-om. I will learn what I can about setting permissions then, once again, pursue how best to approach backup.  
 
 SeijiSensei, I will consider using rsync. I see there are a number of help pages for that method.  
 
 ...still trying to find the answers to life's persistent questions.

---

