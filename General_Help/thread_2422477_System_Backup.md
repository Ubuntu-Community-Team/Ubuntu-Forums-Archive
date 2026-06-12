---
title: "System Backup"
date: 2019-07-08
forum: General Help
---

### Post by kesetyan on 2019-07-08
Hi,
I'm running an Ubuntu 18.04 desktop and need assistance concerning backing up the system and possible restoration.  

I've had some success in backing up and restoring from an image file using the 'Disks' program but I have found that I cannot always create a new image file when I want.  I understand that 'Disks' creates a backup image of a complete partition, including the unused space, and that it requires a copy location of equal size or larger.  My system drive is a 120gb SDD and my save location is an external 160gb HDD.  This arrangement has worked in the past, after I had my computer's motherboard and SDD replaced under warranty, but I can't seem to create new image backup files any more.  I boot the system from a live Ubuntu 18.04 usb memory stick and run 'Disks' but get permissions errors.  I clear all the old material off the external drive and even have tried reformatting it.  Obviously I am doing something wrong but have been unable to work out what.

I have also tried running Clonezilla and have successfully created partition image files on another external drive. So far I have not tried to restore Clonezilla images but am a little concerned after reading somewhere on the internet that the Clonezilla images should be saved in a partition of similar file system.  My external disc drives are formatted NTFS so, presumably, my Clonezilla image files would not be restorable as the Ubuntu partition on the internal SDD is formatted Ext4.

I'd be very grateful for comments, tips and advice that more experienced Ubuntu users can give this 78 year old learner.

Thanks and cheers.

---

### Post by VMC on 2019-07-08
From a terminal try ```
sudo gnome-disks
```

In the future I would backup partitions using *[fsarchiver]("http://www.fsarchiver.org/") , *if they are ext4 partitions.

---

### Post by SeijiSensei on 2019-07-08
I find it much easier simply to back up /home (and any other places you have created files), then just reinstall and copy the backed up files.  I don't find whole-system backups all that useful myself. 

In fact, I keep /home on a separate partition.  Then I just need to reinstall and point the installer to the existing /home partition.

---

### Post by HermanAB on 2019-07-08
Ayup - I don't see the point in recovering an old and tired system from backup, when I can install the latest and greatest version in about 20 minutes.  So I only backup my data.  Doing so, uses far less storage space, enabling me to use versioned backups, which are rather more useful to me.

For example:
mv backup.3 backup.tmp
mv backup.2 backup.3
mv backup.1 backup.2
mv backup.0 backup.1
mv backup.tmp backup.0
cp -al backup.1/. backup.0
rsync -a --delete source_directory/ backup.0/

As explained here: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by kesetyan on 2019-07-08
Hi VMC and SeijiSensei,

Thanks for your quick replies.

I am not having a problem backing up my personal data files and find for that purpose GRsync does a good job with no fuss.  As for system partition backup image files, having been used backing up my former Windows XP and existing Windows 7 systems *(if I'm allowed to mention Microsoft operating systems on this forum)* using the superb Macrium Reflect program, I have perhaps been spoilt as far as system image backups are concerned but I would like to have a means of restoring my Ubuntu system should the worst happen.  I am intrigued by your point Seigi but think you may have misunderstood me.  As I have said, I have no problem with my own data files; in fact I keep virtually all of these on the internal hard drive, it is the operating system partition on the internal SDD for which I wish to create a restorable image file.  I know I could undertake a fresh installation of Ubuntu 18.04 on the SSD if there were a crisis but I would then have to redo all my settings and install programs I have added - I would like to avoid all that hassle if possible. 

Incidently, last year, I changed my Windows 7 Desktop arrangement to a dual boot setup with Lubuntu 18.04 and that has proved interesting.  While I was getting used to Lubuntu I made serious mistakes but was able to recover from them because I used Macrium Reflect in Windows 7 to create image files of all the HDD partitions including Lubuntu and so could restore the Lubuntu partition to a time before I made the errors.  That process worked very smoothly.  Unfortunately my Ubuntu 18.04 system is a stand alone setup so there is no Macrium Reflect rescue facility.

I will try what you suggested VMC as regards opening 'Disks' through a sudo command in the terminal but I would be grateful if you could point me in the direction of a good online instruction page for using 'Disks' as, so far, what I have found has not been very comprehensive particularly with regard to preparing the copy location for the Ubuntu partition image file.

Finally, if Clonezilla is potentially easier and more efficient in use of space, I'd happily use it but would like to know if it is essential for the partition image file to be copied to a location of the same file format as the Ubuntu partition (as was suggested on one web page I read recently).  I am not talking of a clone of the partition here which includes all unused areas of the partition but an image file with the '.img' file extension which copies only used areas.

I hope I have been clear enough in explaining what I am looking for.  All help and suggestions are always gratefully received so thanks again VMC and Seigi.

Cheers.

---

### Post by rbmorse on 2019-07-08
Did you know that that you can use Macrium Reflect to back up your Linux partitions just like you do with the Windows partitions (as long as they're on an ext filesystem)?  You'll have to boot Windows, or use the Macrium backup booter from a flash device, to restore the Linux partition images, but that should not be a big deal.  It'll be slow as Reflect uses bit-copy mode because Linux doesn't have an equivalent to Windows' VSS, but it works fine. 

Clonezilla should be OK.   As long as it can read the image file it should be able to restore it without issues.  NTFS and ext2/3/4 are all supported filesystems.

---

### Post by GhX6GZMB on 2019-07-08
Perhaps this thread helps:

[https://ubuntuforums.org/showthread.php?t=2422217](https://ubuntuforums.org/showthread.php?t=2422217)

---

### Post by RobGoss on 2019-07-08
Nice way to do it for sure,** SeijiSensei's**

---

### Post by Artim on 2019-07-08
That other thread offers some good suggestions!  Including my own favorite - though rarely used - **SystemBack**.  Find it [here]("https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10").

---

### Post by kesetyan on 2019-07-09
Hi All,

I am most impressed and grateful for the number and helpfulness of the responses I have received.

I have resolved my issue by following VMC's suggestion of, after booting from the live Ubuntu usb memory stick, opening Gnome Disks by typing 'sudo gnome-disks' in the terminal.  That worked smoothly for me for me although it took a fair amount of time to complete.  While I appreciate that Gnome Disks is not the most efficient user of storage space, it is simple to use.  The alternative, Clonezilla, uses space more efficiently but I find its interface cluttered and confusing.  Storage space for my Ubuntu partition images is not a problem for me as I have a couple of 160gb hard drives I took from a couple of desktop computers I stripped down.  They easily convert to external usb drives via a powered conversion lead and their capacity is ideal to cope with the nearly 120gb Ubuntu partition.

Backing up my data files has not been a problem, I don't store them on the SDD but on an internal hard drive and GRsync is more than adequate to cope with my regular data backups to the cloud and external devices.

I certainly appreciate the suggestions and links provided and will investigate further as my confidence grows.  Thank you all for helping an old fogey like me.

Cheers and best regards to all.

---

### Post by TheFu on 2019-07-09
Be very careful using NTFS with rsync backups.  On a multi-user system like all Unix-based OSes, the data is only 50% of a backup. We need the owner, group, permissions and ACLs for every file, every directory, every link, every sparse file too.   But rsync for straight media files is probably sufficient, since those will all have 1 owner, 1 group, and 1 set of permissions.  It is the OS, application and their data files where more than just the data is necessary.

I've started to reply to this thread a few times the last few days. Ended up deciding against 'posting' since your desired needs are very different from what I'd consider absolutely required in a backup. 

I'd strongly suggest you take a look at **fsarchiver** for your image-based needs.  It is much more flexible than all the other options I've seen, uses compression and can restore to different sizes partitions/LVs, even smaller than the original.
For a backup:```

/usr/sbin/fsarchiver  -vA -z5 -j2 savefs \
   /media/$USER/target-190710-root-lv.fsa \
   /dev/mapper/ubuntu--vg-root
```  I use LVM, but the mapper part could be /dev/sdaX if you like.  1 backup.fsa file for each partition/LV.
For a restore:
```
/usr/sbin/fsarchiver restfs   \
   /media/$USER/target-190710-root-lv.fsa \
        /dev/mapper/ubuntu--vg-root
```
Obviously, check the manpage for more details and to validate my options.  It has the quiesce problem, which is easily solved by booting from alternate boot.  Some people setup a separate, tiny, ubuntu partition with backup/restore tools on their main HDD. Others use a live-boot flash drive.

I haven't used fsarchiver in a long time. Much prefer using rdiff-backup for many, many, reasons.

---

### Post by kesetyan on 2019-07-10
Hi TheFu,

Thanks for your suggestion, fsarchiver has been mentioned before in this thread so I am seriously considering it.

I've started my investigation of fsarchiver by visiting the webpage.  It seemed that it would be a good idea to download the latest System Rescue iso and create a bootable dvd as it was stated that this would include fsarchiver along with a number of other useful accessories.  I created the live disc which boots fine but I cannot see fsarchiver anywhere on it.  Unless it is only accessible via the terminal, it doesn't appear to be there.

Considering that I'm a 78 year old learner who finds some of the technical language difficult on these matters, how do you suggest I proceed?

Cheers.

---

### Post by TheFu on 2019-07-10
System Rescue is fine, but you'll want to burn a new one every 6 months still.  By staying with an ubuntu Live Boot, you can just run 
**sudo apt-get install fsarchiver** to get the tool you need installed.  10 sec of effort for most people.  It isn't permanent, so every reboot, you'd need to do that.

There is no GUI for fsarchiver.  Put that out of your mind.

Age is just in your mind.  It is desire that matters.  If you want to accomplish it, you know you can.  We're all getting older, fighting with different ailments, but keeping our minds sharp is a personal duty.

You know how you learn best. I'm a visual learner, so I need to read it.  Someone explaining it only works for me after I've read the material.  The fsarchiver manpage is pretty clear.
```
NAME
       fsarchiver - filesystem archiver

DESCRIPTION
       fsarchiver  is  a system tool that allows you to save the contents of a
       filesystem to  a  compressed  archive  file.  The  file-system  can  be
       restored  on  a  partition  which  has  a  different size and it can be
       restored on a different file-system. Unlike  tar/dar,  FSArchiver  also
       creates  the filesystem when it extracts the data to partitions. Every-
       thing is checksummed in the archive in order to protect  the  data.  If
       the  archive  is corrupt, you just lose the current file, not the whole
       archive.
```

If you insist on using image-based backups, fsarchiver is the most capable answer, unless you are a business and need to stream the installs to 20+ systems concurrently.

I still think image-based is the wrong answer for backups for a number of reasons, but it is your setup, not mine.

---

### Post by VMC on 2019-07-10
Actually there is a graphical front end for fsarchiver:
[https://wiki.ubuntuusers.de/qt-fsarchiver/](https://wiki.ubuntuusers.de/qt-fsarchiver/)

I've used it before and was impressed. Somehow the compression was better than I used with *fsarchiver* "-j" option.
But in the end a simple script or a single line *fsarchiver* does the job quickly, and if you have multiple cores, even faster.

---

### Post by kesetyan on 2019-07-10
Hi TheFu and VMC,

Thanks for your continued interest and support.

Other than a bit of dabbling with live discs of various Puppy Linux distributions, running a dual boot setup of Puppy Precise 5.7.1 with Windows XP for a couple of years and running live usb versions of Mint, Ubuntu and other Linux distributions, my experience of Linux is very limited and mainly superficial.  I am open to advice, willing to learn and find the support I get on this forum from members like you very encouraging.  Most of my limited computing knowledge is through a Microsoft Windows perspective although I have realised, particularly with Windows 10, that is not the way forward for me and hence me taking Linux in general and Ubuntu in particular more seriously.  Backing up my system in Windows invariably meant creating partition image files using programs such as Easeus ToDo, Acronis True Image and Macrium Reflect, the latter being my preferred choice and the one I use in my Windows 7 setup.

TheFu, I am intrigued by your strongly put point, that image-based backups are not the answer.  I just want to be able restore the operating system, my settings and installed programs should disaster strike so would be interested to learn more about alternative solutions that won't confuse me too much considering my Linux understanding is still rather limited (I am not a technophile but neither am I a techophobe so am willing to try to learn).  I'm not worried about my data files as they are not stored on the system partition and they are regularly backed up to several different off-computer locations including in 'the cloud'.  In an emergency I could, of course, do a fresh installation of Ubuntu but would have to redo my settings and install the programs I had added before the disaster.

VMC, thanks for the link regarding a GUI for FSArchiver.  My German is non-existant so I might struggle with that but I might give it a go.

Cheers and regards to you both.

---

