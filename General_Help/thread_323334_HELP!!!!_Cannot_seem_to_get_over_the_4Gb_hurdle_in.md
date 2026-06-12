---
title: "HELP!!!! Cannot seem to get over the 4Gb hurdle in doing a system backup."
date: 2006-12-21
forum: General Help
---

### Post by Robertjm on 2006-12-21
Hi all,

I'm having some major issues with trying to do a full system backup.

First I tried using TAR piped to a split command, however, I get one 4Gb file and then the back up stops. Here's my backup.sh file's contents:

tar cvpjf /media/SEA_DISK/BACKUPS/20061217backup.tar.bz2 --exclude=/wine --exclude=/proc --exclude=/lost+found --exclude=/media/SEA_DISK/BACKUPS/20061217backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/temp --exclude=/tmp --exclude=/dev --exclude=/home/.Trash-root --exclude=/home/robertjm/.Trash --exclude=/media --exclude=/var/cache --exclude=/var/tmp --exclude=/home/robertjm/Desktop/Amarok\ Desktop\podcasts /  | split -b 4024m

So next I checked to see what kind of backup software might be available through the repositories. I found KDAR and Mondo.

When using KDAR, I set up all the excludes just like in the above TAR command and chose the DVD-sized chunks so I can burn it to DVDs. Here's the contents of my KDAR "profile" file, which has all the information to perform the hoped for backup:

[Create / Isolate]
compressionAlgorithm=121
compressionLevel=9
compressionMaskList=
compressionMaskType=0
directoryMaskList=/media/SEA_DISK/BACKUPS,/dev,/home/robertjm/Desktop/Amarok music/podcasts,/home/robertjm/.Trash,/home/.Trash-root,/lost+found,/media,/mnt,/proc,/sys,/temp,/tmp,/var/cache,/var/tmp,/wine
directoryMaskTypes=Auto,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude
executeCommand=
executeRef=
fileMaskList=
fileMaskType=0
firstSliceSizeStrings=700,4400,2,870,782,700,650,553,439,298,263,237,202,184,175,1440,100
firstSliceSizeSuffices=2,2,3,2,2,2,2,2,2,2,2,2,2,2,2,1,2
ignoreDump=false
inputPipe=
keepPruned=true
media=1
minimumCompressionSizeInt=150
outputPipe=
passRef=
pauseBetweenSlices=false
sliceSizeString=700
sliceSizeSuffix=2
splitArchive=true

[Cryptography]
cryptoAlgorithm=0
cryptoBlockSize=10240
storePassword=true

[Diff]
hourShiftInt=0

[Extract]
allowOverwrite=true
extractArchiveDirectory=
flatRestore=false
noDelete=true
restoreRecent=true
warnOnOverwrite=false

[Filesystem]
ignoreID=false
systemEA=true
userEA=true

[Fonts]
fileBrowserFont=Sans Serif,10,-1,0,50,0,0,0,0,0
generalFont=Sans Serif,10,-1,0,50,0,0,0,0,0
messageWindowFont=Sans Serif,10,-1,0,50,0,0,0,0,0
statusBarFont=Sans Serif,10,-1,0,50,0,0,0,0,0

[General]
archiveStorageDir=/media/SEA_DISK/BACKUPS/
differentialBackup=false
differentialBackupArchiveName=
directoryToBackup=/
dryRun=false
lastArchive=select archive
logFile=/media/SEA_DISK/BACKUPS/kdar/kdar.log
logLevel=1
newArchiveName=20061218_full
showKDarSplashScreen=true
useCreateArchiveWizard=true
verbose=true


Again, one 4Gb chunk and that was it.

Finally, I tried Mondo. Lord knows what happened there as I got ONE 1.5Gb .iso file and that was it. I certainly don't believe I got a full backup with that file. I'm trying to do a full system backup at first and there's somewhere around 20Gb of data, give or take a few Gb, that would be backup up.

I'm backup up to a 250Gb external drive, which is split. The first part is formatted FAT32, and the second part is formatted NTSF. I am writing the backup to the FAT32 partition. My understanding with the split command is that it starts writing and then once it gets to the predefined size it finishes writing the first split and starts writing the second split, third split, etc. Am I mistaken?

What are others doing for full system backups? At the present time I can't reformat the external drive to ext2/ext3 because I've got some stuff on the NTSF partition I can't offload and I can't afford another external drive.

Any suggestions for my situation?

---

### Post by Rippey on 2006-12-21
fat32 doesn't support files over 4gb, making your back up in chunks that are just under 4gb and you should have no problems.

---

### Post by tagra123 on 2006-12-22
> **Robertjm said:**
> Hi all,

I'm having some major issues with trying to do a full system backup.

First I tried using TAR piped to a split command, however, I get one 4Gb file and then the back up stops. Here's my backup.sh file's contents:

tar cvpjf /media/SEA_DISK/BACKUPS/20061217backup.tar.bz2 --exclude=/wine --exclude=/proc --exclude=/lost+found --exclude=/media/SEA_DISK/BACKUPS/20061217backup.tar.bz2 --exclude=/mnt --exclude=/sys --exclude=/temp --exclude=/tmp --exclude=/dev --exclude=/home/.Trash-root --exclude=/home/robertjm/.Trash --exclude=/media --exclude=/var/cache --exclude=/var/tmp --exclude=/home/robertjm/Desktop/Amarok\ Desktop\podcasts /  | split -b 4024m

So next I checked to see what kind of backup software might be available through the repositories. I found KDAR and Mondo.

When using KDAR, I set up all the excludes just like in the above TAR command and chose the DVD-sized chunks so I can burn it to DVDs. Here's the contents of my KDAR "profile" file, which has all the information to perform the hoped for backup:

[Create / Isolate]
compressionAlgorithm=121
compressionLevel=9
compressionMaskList=
compressionMaskType=0
directoryMaskList=/media/SEA_DISK/BACKUPS,/dev,/home/robertjm/Desktop/Amarok music/podcasts,/home/robertjm/.Trash,/home/.Trash-root,/lost+found,/media,/mnt,/proc,/sys,/temp,/tmp,/var/cache,/var/tmp,/wine
directoryMaskTypes=Auto,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude,Exclude
executeCommand=
executeRef=
fileMaskList=
fileMaskType=0
firstSliceSizeStrings=700,4400,2,870,782,700,650,553,439,298,263,237,202,184,175,1440,100
firstSliceSizeSuffices=2,2,3,2,2,2,2,2,2,2,2,2,2,2,2,1,2
ignoreDump=false
inputPipe=
keepPruned=true
media=1
minimumCompressionSizeInt=150
outputPipe=
passRef=
pauseBetweenSlices=false
sliceSizeString=700
sliceSizeSuffix=2
splitArchive=true

[Cryptography]
cryptoAlgorithm=0
cryptoBlockSize=10240
storePassword=true

[Diff]
hourShiftInt=0

[Extract]
allowOverwrite=true
extractArchiveDirectory=
flatRestore=false
noDelete=true
restoreRecent=true
warnOnOverwrite=false

[Filesystem]
ignoreID=false
systemEA=true
userEA=true

[Fonts]
fileBrowserFont=Sans Serif,10,-1,0,50,0,0,0,0,0
generalFont=Sans Serif,10,-1,0,50,0,0,0,0,0
messageWindowFont=Sans Serif,10,-1,0,50,0,0,0,0,0
statusBarFont=Sans Serif,10,-1,0,50,0,0,0,0,0

[General]
archiveStorageDir=/media/SEA_DISK/BACKUPS/
differentialBackup=false
differentialBackupArchiveName=
directoryToBackup=/
dryRun=false
lastArchive=select archive
logFile=/media/SEA_DISK/BACKUPS/kdar/kdar.log
logLevel=1
newArchiveName=20061218_full
showKDarSplashScreen=true
useCreateArchiveWizard=true
verbose=true


Again, one 4Gb chunk and that was it.

Finally, I tried Mondo. Lord knows what happened there as I got ONE 1.5Gb .iso file and that was it. I certainly don't believe I got a full backup with that file. I'm trying to do a full system backup at first and there's somewhere around 20Gb of data, give or take a few Gb, that would be backup up.

I'm backup up to a 250Gb external drive, which is split. The first part is formatted FAT32, and the second part is formatted NTSF. I am writing the backup to the FAT32 partition. My understanding with the split command is that it starts writing and then once it gets to the predefined size it finishes writing the first split and starts writing the second split, third split, etc. Am I mistaken?

What are others doing for full system backups? At the present time I can't reformat the external drive to ext2/ext3 because I've got some stuff on the NTSF partition I can't offload and I can't afford another external drive.

Any suggestions for my situation?


I have answered in another post, something that may help you.  Partimage allows you to specify the size of the backups and will automatically split the files to the size you specify.

[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

---

