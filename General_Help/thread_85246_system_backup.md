---
title: "system backup"
date: 2005-11-02
forum: General Help
---

### Post by jrev on 2005-11-02
Hi all,
I would appreciate to know which application you are using to back up your system.
How does it work ?
How long have you been using it ?
Are you satisfied ?
you aren't using any ?
:???:

---

### Post by frodon on 2005-11-02
Personnaly i use norton ghost because i have it already before ubuntu (it's not free) and it works really well.
However [mondo]("http://www.mondorescue.org/about/about.html") is a good tool for backup and i know persons here who use it with success.
These threads contain a lot of informations you're looking for : 
[http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

### Post by jrev on 2005-11-02
Thanks for the addresses...

---

### Post by clems[ on 2005-11-02
hi,

For me i test sbackup it's very friendly.
Just do apt-get install sbackup

_[http://linux.softpedia.com/get/System/Backup/SBackup-4630.shtml](http://linux.softpedia.com/get/System/Backup/SBackup-4630.shtml)_

---

### Post by pickarooney on 2005-11-02
testing sbackup at the moment - how do you know when the backup is complete?

---

### Post by frenkel on 2005-11-02
I juse just tar and it rules!!
You can use it like this:
Boot with a livecd (any will do, Ubuntu livecd, Knoppix, Gentoo, it's your choice!)
Mount the partitions. (In this example /mnt/root is my Ubuntu install and /mnt/backup is my backup paritition).
Then run this:
# cd /mnt/root

For a normal tar:
# tar -cjvpf /mnt/backup/backup.tar.bz2 .
Or split it in chunks of 1024 MB, when backup up to FAT32 for example:
# tar -cjvp . | split -b 1024m - /mnt/backup/backup.tar.bz2.
This will create files like backup.tar.bz2.aa backup.tar.bz2.ab backup.tar.bz2.ac

Restoring can be done like this:
# cd /mnt/root
For a normal tar:
# tar -xjvpf /mnt/backup/backup.tar.bz2
For a splitted tar:
# cat /mnt/backup/backup.tar.bz2.?? | tar -xjvp

Good luck!!

---

### Post by pickarooney on 2005-11-02
Ack, I think I did something wrong and now my / partition is 100% saturated. :(
Can someone help me find the backup I just made with simple backup config?
I can't open any thing, even man pages at the moment, as there's no space.
I told sbackup to make the backup on /media/hdb5 (empty 50GB partition) but it seems to have made it somewhere in the system root.

---

### Post by crowndip on 2005-11-02
Hi guys,

i am using g4l and it's great.

it can take all disk data, compress them und upload them on an ftp server.
very easy and free

it can of course put the image also on another disk.

the main advantage is that it does not need to understand the filesystem of the backed up disk - it just takes all data as they are.

my 20 GB notebook disk is compressed to 1.2 GB

enjoy
Filip

---

### Post by LittleReinhart on 2005-11-02
Hey, [QUOTE=jrev]Hi all,
I would appreciate to know which application you are using to back up your system.
How does it work ?
How long have you been using it ?
Are you satisfied ?[/QUOTE]
Long time ago , in my old windows days (after booting from bootdisk/bootcd)
```
<a:\> xcopy /s /c /h /r /e /k c:\*.* d:\backup\*.*
```
This workes for drives formatted in fat32 (doesn't work for ntfs)
I'm not shure anymore what the /x things stand for anymore, but it just copies everything (including system and hidden files).
Anyway, pro's: it works from the command line ;-)
contra: the backup is as big as the file-system

A few years later, I found out about norton Ghost, liked it a lot. (especially the compression option)

Now I use linux for half a year now, and from the beginning I learned the dd command
I boot from an other linux partition (or knoppix/dsl cd)
```

mount /dev/sda2 /mnt/sda2
dd if=/dev/zero of=/mnt/sda2/bigfile  # this is to write zero's to all empty space. It can take a while (depending on the size of your partition)
sync
rm /mnt/sda2/bigfile
sync 
umount /mnt/sda2
mount /mnt/sda3
dd if=/dev/sda2 | gzip -c > /mnt/sda3/newBackup/backup-ubuntu-5.10-x.img.gz

```
I use this for half a year now... and I realy love this, cus it combines the best of the other two above!

Edit: I'm sorry, I forgot to mention... if you take a backup, there comes a moment you want to put the backup back (boot from a knoppixcd or something like that):
```
mount /mnt/sda3
gzip -cd /mnt/sda3/newBackup/backup-ubuntu-5.10-x.img.gz | dd of=/dev/sda2 
```

Greetings,
Reinhart

---

### Post by jrev on 2005-11-02
I got some hope from your new tracks.
thanks everybody :smile:

---

### Post by BlueNoteMKVI on 2005-11-12
Check out Dirvish ([http://www.dirvish.org]("http://www.dirvish.org")) for automatic incremental backups.

---

### Post by SickTwist on 2005-11-12
[QUOTE=pickarooney]Ack, I think I did something wrong and now my / partition is 100% saturated. :(
Can someone help me find the backup I just made with simple backup config?
I can't open any thing, even man pages at the moment, as there's no space.
I told sbackup to make the backup on /media/hdb5 (empty 50GB partition) but it seems to have made it somewhere in the system root.[/QUOTE]

You could run "sudo apt-get clean" (without quotes) to remove the packages that have already been installed. (This does not uninstall anything, it just removes the package used to do the installation.)

Also, the backup may have been saved in /media/hdb5 on the / filesystem if the 50 GB partition was not mounted. Unmount the 50 GB partition and check this directory.

---

