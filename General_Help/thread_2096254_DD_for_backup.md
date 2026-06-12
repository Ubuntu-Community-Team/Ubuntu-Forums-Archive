---
title: "DD for backup"
date: 2012-12-19
forum: General Help
---

### Post by eslavko on 2012-12-19
Hello... 
Just wake up from hard drive failure.
As drive isn't totaly death (just response slow and s.m.a.r.t report a lot of udma errors) I just clone that drive to external usb harddrive with DD utility, and restore after harddrive replacement (still in warranty)
I Just type 
```
sudo dd if=/dev/hda of=/dev/sdc bs=64k conf=notrunc,noerror

```
and for restoring just swap sda and sdc drive.
Work perfect and I have all stuf ready after two hour after got computer from service.
Now I search if it's possible to do near same operation but without need to reformat backup disc?
Ie to copy all sectors from source disc to the destination file (file not disc) and perheaps to compress it too. I found some examples to make iso file or gzip but just for input partition and not the drive.

I had daily backup for data but now want to make monthly for entire drive. It's not fun to search what drivers and application are on old lost drive.

---

### Post by oldfred on 2012-12-19
I prefer new clean install, but backup whatever else I need in the way of info with rsync.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

    
       Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/12.04/serverguide/C/backup-shellscripts.html)
But do not use dd for copies from MBR to gpt partitioned drives
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)
If you don't mind the command line, you can use duplicity.
If you DO mind the command line, there is a front end for duplicity; deja-dup.
AIR - Automated Image and Restore 
AIR is a GUI front-end to dd/dc3dd designed for easily creating forensic images. by Steve Gibson and Nanni Bassetti
    
       Files that may need update on image copy
 fstab, reinstall grub and grub's reinstall location. Or change UUIDs
If different computer:
/etc/hostname and /etc/hosts,
    
       Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh

    
       [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

            Other applications if data not separate
apache, any sqldb, tomcat, web folders, etc

            Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
            More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

            Some more examples:
[http://rsync.samba.org/examples.html](http://rsync.samba.org/examples.html)

---

### Post by 1clue on 2012-12-19
+1 on rsync, or even just dragging the folders over with your mouse.

Been in computing since the mid '80s, tried all sorts of backup mechanisms.  Then I had to use one, and realized that it didn't make a restorable backup, making all that time spent making the backups worthless.

Right now I have a removable drive (a SATA bay, you just stick a bare internal drive into the slot) and I drag interesting files over to the backup device, inside of a folder whose name is the date of the backup.  No compression, just normal data.  That way one corrupted byte doesn't invalidate a whole backup.

---

### Post by eslavko on 2012-12-20
For daily backup I use rdiff-backup. But for backup of full disc clone it's not ussable. (mbr's partition tables etc..)

I search a lot of backup software but just rdiff make version history and work fast. (well deja-dup work that too but is so slow..)

---

