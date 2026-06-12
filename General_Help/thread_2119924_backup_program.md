---
title: "backup program"
date: 2013-02-25
forum: General Help
---

### Post by GameX2 on 2013-02-25
Hi,

I've tried many different backups programs, and I find it hard to find a backup program that fit my needs..  I should mention that I'm a novice about backup under Linux, and that I've never configured backups myself. :P
On our Windows family PC, my father, the administrator always used to configure the backup.

I've used Acronis True Image Home 2009, to create system images of EXT2 partitions.  Unfortunately, the 2009 version does not support EXT3/4.
I've also tried LuckyBackup (LiveCD) which look really good.  It create an image of a partition, but technically, not stored in just 1 file.  It has great compression.

Tried Clonezilla, as well.  The LiveCD is in command-line, which I found confusing.
I would prefer to use a GUI tool instead of a LiveCD; I sure don't want to boot a LiveCD manually every week.

I should mention that I backup my files on a NTFS external drive; I've tried BackInTime and LuckyBackup (Interesting.  It use Rsync).  LuckyBackup got my interest, until I found the backup was sync in both way.  Could I just sync from Home to the External drive, not the reverse?  Also had trouble to configure snapshots...

The biggest problem has to be file permissions; I don't know if it's a Linux limitation, but backing up all my "Home" to my NTFS external drive wiped all my file permissions (And so the scripts that are marked as "executables" are not working).  Is there a way to fix this?  Maybe compressing the backup in an archive (Later extracted by the backup program) would help?

Please, do you have any suggestions?
(I would prefer to avoid all command-line based tools, unless that's easy.  I do not fear the command-line, but for complete softwares that's more complicated.  I do not want to screw anything up, especially with backups.)

I would love a tool that has backup compression if possible, and with the option of creating differential backups.  Week 1, full backup.  Week 2, second snapshot which save only the differences.  Then I'll be able to restore that in an easy way, I hope.

Second question, how often do you backup your Root ( / ) partition ?

Thanks!

---

### Post by HermanAB on 2013-02-25
It is called rsync.  Read the man page.  

Almost all fancy Linux backup programs use rsync underneath.  

If you would bother to read the man page, then you will see that all these backup programs just make things more difficult, instead of easier.  Therefore, everyone that knows anything eventually make their own one line scripts with rsync and only the newbs use the fancy backup programs.

---

### Post by codemaniac on 2013-02-25
You can find the below wiki useful.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by ajgreeny on 2013-02-25
Whilst HermanAB has a good point, and making a script and running it regularly with cron is easy, I think there is nothing wrong using grsync, which as the name implies is just a gnome GUI for rsync.

This is what I use for backing up my home partition files and folders; I do not bother backing up the OS itself as it is so easy to re-install if you have a separate home partition.

---

### Post by GameX2 on 2013-02-25
Thanks, I've found interesting informations here (In French - my main language):
[http://doc.ubuntu-fr.org/tutoriel/sauvegarder_home_avec_rsync](http://doc.ubuntu-fr.org/tutoriel/sauvegarder_home_avec_rsync)

My main concern is that I'm backing up to a NTFS external drive (No choice), I will loose my file permissions.  Any way to fix this?  Perhaps save the original file permissions in a text file, then rearrange the permissions from this file, when the backup will be restored ?

If I understand, the only reason why LuckyBackup did a 2-ways syncing, it was because it was programmed to launch Rsync twice?

rsync /source/folder /destination/folder
rsync /destination/folder /source/folder

Is that correct?

As for backing up the system, I assume only a single working image would be fine.
Since reinstallating the softwares is seriously easy and fast, if the vast majority of the users here don't backup " / ", I probably wouldn't bother.

Thanks for the replies!

---

### Post by dave0109 on 2013-02-25
You can set LuckyBackup to only do it one way, it does not have to be a full sync.

As for the permissions, that's an issue with NTFS which doesn't have such a concept.  For this reason, I use BackInTime mostly, which will write the permissions out to a separate file, so that if you need to restore, the permissions can also be restored.

I do occasionally backup the whole disc (exluding some temporary or special device directories), but it's /home that I backup regularly.

---

### Post by lmarmisa on 2013-02-25
> **GameX2 said:**
> Thanks, I've found interesting informations here (In French - my main language):
[http://doc.ubuntu-fr.org/tutoriel/sauvegarder_home_avec_rsync](http://doc.ubuntu-fr.org/tutoriel/sauvegarder_home_avec_rsync)

My main concern is that I'm backing up to a NTFS external drive (No choice), I will loose my file permissions.  Any way to fix this?  Perhaps save the original file permissions in a text file, then rearrange the permissions from this file, when the backup will be restored ?

If I understand, the only reason why LuckyBackup did a 2-ways syncing, it was because it was programmed to launch Rsync twice?

rsync /source/folder /destination/folder
rsync /destination/folder /source/folder

Is that correct?

As for backing up the system, I assume only a single working image would be fine.
Since reinstallating the softwares is seriously easy and fast, if the vast majority of the users here don't backup " / ", I probably wouldn't bother.

Thanks for the replies!

For a full backup of the system I recommend Clonezilla. BTW, Clonezilla has a friendly menu. So command line is only an option.

If you wish to backup the files of your account, you could use the classic command "tar":

```

tar cvf /media/backupdrive/`whoami``date +"%F-%H%M%S"`.tar -C ~ .

```This alternative command will include compression:

```

tar cjvf /media/backupdrive/`whoami``date +"%F-%H%M%S"`.tar.bz2 -C ~ .

```The command tar will preserve file permissions.

An additional comment: files backuped are not 100% reliable if applications are not stopped.

---

### Post by mastablasta on 2013-02-25
> **GameX2 said:**
>  
Tried Clonezilla, as well. The LiveCD is in command-line, which I found confusing.
I would prefer to use a GUI tool instead of a LiveCD; I sure don't want to boot a LiveCD manually every week.

 
as others mentioned rsync (or grsync if you want the GUI) can easilly do what you want. you can set a script that is run every week and do what you want.
 
anyway as for clonezilla the same thing that does manual bare metal backup is RedoBackup. it uses same tools as clonezilla for the most part but it offers a GUI instead of those strange menues found in Clonezilla with little explanation and no choice of going back after option is selected. 
i have to say i haven't done linux image yet with it but i did the WinXP image and it works well. 
 
Clonezilla is a powerfull tool but it's not intuitive and you need to know what you are doing and what means what before you start using it.

---

### Post by LewisTM on 2013-02-25
There was a similar [thread]("http://ubuntuforums.org/showthread.php?t=2106634") a few weeks ago about how to preserve file permissions on a Windows filesystem.

My suggestion was to use **metastore**. It will dump all file metadata in a regular text file which can be backed up along with the rest and used to reapply in the event of a data restore. It's commandline but it's dead simple (only two parameters, Store or Apply).

Another solution that I use for backing up to a corporate Windows network share (so again no Linux permissions) is to create a large loopfile containing a Linux filesystem (ext4, btrfs, xfs). You can mount this loopfile as a regular volume
```
sudo mount -o loop /path/loopfile /mountpoint
```
Then execute your backup. The drawback is that Windows users won't be able to see the contents of the loopfile.

tar will also work nicely if you don't mind working with archives. I prefer to see all backed up files, sync them and keep a few snapshots. That's the selling point of rsync derivatives.

Cheers!

---

### Post by GameX2 on 2013-02-25
> **LewisTM said:**
> There was a similar [thread]("http://ubuntuforums.org/showthread.php?t=2106634") a few weeks ago about how to preserve file permissions on a Windows filesystem.

My suggestion was to use **metastore**. It will dump all file metadata in a regular text file which can be backed up along with the rest and used to reapply in the event of a data restore. It's commandline but it's dead simple (only two parameters, Store or Apply).

Another solution that I use for backing up to a corporate Windows network share (so again no Linux permissions) is to create a large loopfile containing a Linux filesystem (ext4, btrfs, xfs). You can mount this loopfile as a regular volume
```
sudo mount -o loop /path/loopfile /mountpoint
```Then execute your backup. The drawback is that Windows users won't be able to see the contents of the loopfile.

tar will also work nicely if you don't mind working with archives. I prefer to see all backed up files, sync them and keep a few snapshots. That's the selling point of rsync derivatives.

Cheers!

Thanks!

> **LewisTM said:**
> There is an alternative to dumping a Linux fs  onto a Windows drive with tarballs or loopfiles. You can use **Metastore** which is in the repos.

Metastore saves extra Linux file metadata (owner, group, permissions,  extended attributes) in a separate file. You can thus store the metadata  of a file tree as a regular file on a Windows environment (FAT, NTFS,  Samba). The same tool can be used to reapply the metadata once you have  restored the backup onto a Linux fs.

Say you want to backup /home/foo
Just cd to the directory and save the metadata. You shouldn't need sudo unless you don't have read access to some files
```
cd /home/foo
metastore -s
```The metadata will be stored in /home/foo/.metadata
You can now backup /home/foo with rsync or your favorite backup  software. You can ignore any setting regarding saving attributes, you  just need to backup the files.
To re-apply the metadata, restore your files into /home/foo and execute
```
metastore -a
```Remember to run 'metastore -s' before every sync.
It can even be useful in the context of tar. I use user extended  attributes (xattr) a lot and Ubuntu's version of tar doesn't store them.  Putting the .metadata file in the tarball solves that limitation.

Cheers!

That's so easy?  That's all ? :O
Well, that's awesome. :D

This backup command look interesting.  I'll make a script after a few tests:

```
#!/bin/bash

#sudo apt-get install metastore - installed it first
#Check if external drive is mounted
if [ ! -e "/media/GAMEX-DRIVE/Backups/Ubuntu_Home" ]
then
echo "The external drive is not connected.  Please plug the drive."
exit

cd /home/gamex
metastore -s
rsync -rltgoDv --del --ignore-errors --force --progress /home/gamex/ /media/GAMEX-DRIVE/Backups/Ubuntu_Home

#-r : Recursive search
#-l : Copy all symbolic links
#-t : Keep dates
#-g: Keep groups
#-o: Define source owner the same as destination owner
#-D : Keep drives (To be honnest, I found the script on Ubuntu-FR.  What's the purpose of having this for a HOME backup ??)
#-v: Sorry, don't know the meaning in English..
#--del : Delete destination files that do not exist anymore on the source
#--ignore-errors : Self-explanatory
#--force: Force deletion of directories
#--progress: Display Sync progress

echo "Backup finished !  Exiting..."
sleep 3
```I'll add a Cron task for the first time, next.  It is explained clearly on Ubuntu-FR, I'll check.  Did I forgot something in the script?

If you have any suggestion of code I could add, please tell me.
( When the external drive is not connected, I would like to wait for the external drive to be connected, instead of exiting the script - and cancelling my weekly backup.  How do I do this ? )

Thanks, that's really helpful. :)

---

### Post by LewisTM on 2013-02-25
You have the general idea.
You should add fi after your conditional exit command.
The -Dgo rsync parameters won't work in NTFS, these are Linux-specific attributes. You'll get errors but you have set rsync to ignore them so yeah.
Other than that the script should run pretty well. Good luck!

---

### Post by GameX2 on 2013-02-25
Cool, that's why Linux is awesome, as usual. :D

I've done ressearch, and I assume the exclude switch work like this (Excluding a virtual machine):

```
#!/bin/bash

#sudo apt-get install metastore - installed it first
#Check if external drive is mounted
if [ ! -e "/media/GAMEX-DRIVE/Backups/Ubuntu_Home" ]
then
echo "The external drive is not connected.  Please plug the drive."
exit
fi

cd /home/gamex
metastore -s
rsync -rltgoDv --del --ignore-errors --exclude 'VirtualBox VMs/Windows XP x64' --force --progress /home/gamex/ /media/GAMEX-DRIVE/Backups/Ubuntu_Home

#-r : Recursive search
#-l : Copy all symbolic links
#-t : Keep dates
#-g: Keep groups
#-o: Define source owner the same as destination owner
#-D : Keep drives (To be honnest, I found the script on Ubuntu-FR.  What's the purpose of having this for a HOME backup ??)
#-v: Sorry, don't know the meaning in English..
#--del : Delete destination files that do not exist anymore on the source
#--ignore-errors : Self-explanatory
#--force: Force deletion of directories
#--progress: Display Sync progress

echo "Backup finished !  Exiting..."
sleep 3
exit
```If anyone know how to wait until the external drive is connected, please let me know. ;)
I'll do a few tests and let you know how it goes !
Thanks!

---

### Post by HermanAB on 2013-02-25
A few tips:
Don't backup the system, only backup your data.
Don't specify in detail what to backup. Rather exclude the stuff you don't want to backup.
If your backup script is more than one line, then you are doing it wrong.

---

