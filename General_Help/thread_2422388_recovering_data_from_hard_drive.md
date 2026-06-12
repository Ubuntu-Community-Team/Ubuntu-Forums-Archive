---
title: "recovering data from hard drive"
date: 2019-07-06
forum: General Help
---

### Post by jgw on 2019-07-06
I have searched this site for hard drive data recovery and found a huge number of responses.  My problem is which is the easiest and best.  I have cleverly managed to delete a 2tb hard drive.  This is the second drive on my system (not the one I boot from) and holds data of one sort or another.  I first thought I would try testdrive as that seems to be popular.  My problem  is that it seems to deal with the partition.  The partition is fine.  I then wint to gparted and thought to use that to recover my stuff.  It told me that I had an ext file system and thinks, I think, that the file syste  holds 1048575MiB of data which is close to half the drive and sounds about right.  

As far as I can tell gparted will, in theory, check the file system, see what is there, and give me a list of what it found with the option to either mount stuff (hopefully that means recover back to where it was) in the list or copy it someplace else.  My problem is confusion.  Googling, or searching this forum, seems to have literally hundreds of solutions and that confuses.  I really don't want to lose anything on this drive that I don't have to.  That being the case I figured I would post this and, hopefully, somebody will tell me this is the way to go.

Thank you...................

---

### Post by oldfred on 2019-07-06
Many suggest imaging drive to another drive and only work on the image. Then if for some reason you further damage it, you still have original to start over with again.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
Screenshots of several of the recovery tools
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) 
    
If you can mount the partition(s), and you know they are ext4, you can run fsck to repair partition.

       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by fragglebliss on 2019-07-06
I read and re-read your post and don't understand what the problem is with using Testdisk to recover the data. As everything you've described seems like there is no problem with it seeing the data. Testdisk can recover data from either a partition or the entire disk. Just make sure you're running it as su (or sudo). It just takes a long time. But if you value your data, then I guess the recovery of the data is the most important aspect over the duration it takes for the recovery.

My tip, in future, make sure you backup any important data. I have lost much data myself in the past so I understand the feeling. So I'm not going to flame you for not backing up like some members on the forum would because backing up is something we all talk about but most of us are unwilling to admit just how hopeless we all are at ensuring we do it.

---

### Post by jgw on 2019-07-06
Thank you for the reply.  

I keep seeing stuff about partitions.  I understand what they are but I don't think they have anything to do with my problem.  This happened when I erased some files on my main (boot) drive.   [I] just went to my terminal and started running through what I did.  Here was the idiot thing that I did:
mnt/05b9fa40-ab8f-4bca-a003-e813169d7e41$ sudo rm -r 05b9fa40-ab8f-4bca-a003-e813169d7e41  (don't ask why, there is no reason other than not paying attention (kinda humiliating))

What I did was, basically, erase everything on the drive!   I,know that gparted can probably find most of the stuff.  If that is true I need to know if, when the gparted directions say "After the scan you can mount any discovered file systems and copy the data to other media." I am assuming that by "mount" means make the data accessable from the drive I cleverly erased.  I am also including the info on the drive that is displayed in gparted.  Please note that what I erased is exactly what gparted sees as what is mounted.  I have attached information on that drive/partition from gparted.

I also took a look at testdisk.  That one made me a bit nervous.  When I run it that program tells me I have an intel/pc partition which may actually be so but I can't remember what gparted did when I installed it (several years ago)  I also don't know what the rm command does when it removes something.  I suspect it changes a bit someplace but I really don't have a clue  (this whole mess kinda proves that one)

Anyway...................

---

### Post by oldfred on 2019-07-06
I believe parted/gparted is then just offering to run fsck on you sdb1 partition.
But if you used rm to delete everything, then the fsck will not recover anything either. It will just prepare partition for use.

You may need to use photorec. 
I have used it, but on a much smaller partition. It took overnight to run. And it did recovery every file, part of a file and many deleted copies of files. I had as many as 10 copies of same text file. I did have an old backup and had to run many comparisons to try to see which was most updated. It tooks weeks to compare all the files I wanted. I also then learned the hard way to have better backups.

       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html) 
   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by fragglebliss on 2019-07-06
As mentioned above, if you've deleted the data on the disk, which it appears you have, then gparted isn't the tool you need. That is a disk formatting and partitioning package, not a data recovery package. Testdisk is what you need.

---

### Post by HermanAB on 2019-07-06
Gparted is a partition editor, not a deleted file recovery tool.

---

### Post by dragonfly41 on 2019-07-07
> [COLOR=#000000]I have cleverly managed to delete a 2tb hard drive.[/COLOR]

Testdisk is a valuable tool but there are others to try. Search "forensic data recovery" in this forum.

Some points perhaps not evident in first reading the testdisk documents ..

- The target drive you are seeking to recover must not be mounted
- You will need a LiveUSB in which testdisk has been installed and to use this to scan your target drive.
- You will need to purchase another 2TB drive into which any files recovered by testdisk can be saved
- You will need to first format (ext4) the newly purchased 2TB drive.
- The scan by testdisk might take many hours (possibly overnight) to complete and should not be be interrupted or paused.
- Although you may end up having two 2TB drives, one benefit is that you can use one for frequent backups.

---

### Post by jgw on 2019-07-07
Thank you for all the replies!

OK, I will use Testdisk.  I still have some questions (little paranoid <g>)

In my previous post I attached what gparted had to say about the drive to be recovered.  One of the more interesting things is that gparted things that I was only using 32gb out of that drive.  I have no idea if that is right and I will find out but just thought I would mention that.  

Here are some instructions I found online:
[https://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2](https://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2)
[https://vitux.com/how-to-recover-deleted-files-in-ubuntu-through-testdisk/](https://vitux.com/how-to-recover-deleted-files-in-ubuntu-through-testdisk/)

I tend to want to use the first one.  In a couple of the replies above I notice that the drive being recovered should not be mounted.  The strange thing is that any directions I have seen don't tell the user that but I assume it should not be mounted.
I will first have to format and set the file system (ext4) in the new drive.  After that I will remove the drive to be recovered and put the new one in its place.  Then I will take the drive to be recovered and attach it to the computer by usb.  I could go the other way around but given that the new one will get there eventually just thought I would do that.  

Then I will check with Disks to make sure everything is recognized and also unmount the drive to be recovered.  
Then run Testdisk and:
choose no recording
Click on advanced
click on undelete and then choose the folders to undelete
Then there are a couple other options.
**Do I want to hide deleted files?**
After that press 'c' to Copy
Stand back and wait for it to finish.Hopefully I have all this right.  Especially the not mounted thing.

Any other thoughts anybody has would be of interest - I really don't want to screw this one up!

Thanks!

---

### Post by dragonfly41 on 2019-07-07
If you plan to swap out drives and reinstall OS (sans your lost data) then this makes sense since you will not then need a LiveUSB
running testdisk. Testdisk can be installed on your fresh Ubuntu installation. 

You might consider experimenting with a dry run on a smaller drive such as USB (not your target drive you are trying to recover) to become familiar with the recovery process, in particular the final stage of saving recovered files. Also explore the dumping of a log file.  With testdisk installed run ```
testdisk --help
``` to see the options.

Also take some time browsing the cgsecurity forum.  Post a question to that forum if you have any issues.

I confirm advice to recover data from an unmounted drive.

[p.s] Remember hidden files. And also remember that there might be files which you intentionally deleted.

---

### Post by dragonfly41 on 2019-07-09
Here is an added nugget of information I found in cgsecurity forum ..

[https://forum.cgsecurity.org/phpBB3/viewtopic.php?f=4&t=2147](https://forum.cgsecurity.org/phpBB3/viewtopic.php?f=4&t=2147)

> [COLOR=#333333][FONT=&quot]When a file is deleted from an ext3 and ext4 filesystem, the location of the first block is zeroed, so TestDisk can list all filenames, deleted or not, but it's not possible to undelete them. PhotoRec can be use to recover files with known filetypes from the free space of the filesystem and recover them but without the original filenames.[/FONT][/COLOR]

This suggests that deleted files in ext4 formatted partition might not be recoverable, but the filenames are recoverable.
This leaves only PhotoRec as your option but PhotoRec does not provide filenames. 

Another option to try is [R-Linux]("https://www.r-studio.com/free-linux-recovery/").

---

### Post by jgw on 2019-07-09
OK, I have started testdisk and got to advanced and ran into a problem.  I have posted a picture of it.  The problem is that it only seems to see my backups from my main drive!  (there is no undelete option).  There was a lot  more stuff on that drive that the backups.  IMy options were actually:
 [  Type  ] >[Superblock]  [  List  ]  [Image Creation]  [  Quit  ] superblock was highlighted.  

This is what I deleted: mnt/05b9fa40-ab8f-4bca-a003-e813169d7e41$ sudo rm -r 05b9fa40-ab8f-4bca-a003-e813169d7e41  (I deleted EVERYTHING!)

Any thoughts?

---

### Post by dragonfly41 on 2019-07-09
Other ideas .. but only from searching around so no guarantees that they might help ..

My further reading suggests that it might be hard to recover ext4 formatted partitions.

Also try R-Linux as suggested earlier.

I have read about ext4undelete.

[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

This tool is in Ubuntu repository.

Reading here ...

[https://askubuntu.com/questions/217606/undelete-files-on-ext4](https://askubuntu.com/questions/217606/undelete-files-on-ext4)

see AnalyzeEXT/

The following video is a forensic investigator's explanation of how to forensically recover data after the rm command has been used.

[https://www.youtube.com/watch?v=6pzm6909IvY](https://www.youtube.com/watch?v=6pzm6909IvY)


There is a script discussed at the very end of this video.

[https://github.com/halpomeranz/analyzeEXT/blob/master/analyzeEXT.pl](https://github.com/halpomeranz/analyzeEXT/blob/master/analyzeEXT.pl)

---

### Post by jgw on 2019-07-09
Thank you for the reply and information.

I suspect that I will be making a run at extundelete.  Apparently one can use that without messing with the actual data on the drive.  I watched the video by the forensic investigative which was waaay past my paygrade.  I also, in theory, posted a query on the cgsecurity forum.  I say in theory as I can't find it and will probably have to post it again tomorrow.  

My main problem, now, is to first figure out just what I did!  testdisk, for instance, can only find my backup files which is in something called a superblock.  I am not sure but I may have actually deleted a partition  with rm, something I didn't know was even possible.  Given that I am seriously confused I need more information.  I will attack this one tomorrow.  

I also have a problem with references to partition types and filetypes.  I had to prepare a new 2tb drive to receive recovered (hopefully) files.  I used a partition type of GPT because of the 2tb size.  The filetype, however, will be ext.  My problem is, I think, that this is referred to as an "ext partition".  Gets a bit confusing.  If it was a smaller drive it would probably get a partition type of MSDOS and the filetype would remain 'ext'.  Both, however, would seem to be called EXT partitions.  A bit confusing, I think.

Anyway, tomorrow is a new day - will see what happens next.

Thanks again!

---

### Post by dragonfly41 on 2019-07-10
> [COLOR=#000000]My main problem, now, is to first figure out just what I did!

[/COLOR]If you are not sure what damaging command you used (including rm) you can inspect the history of all commands executed.

```
history
``` will give a list of every command.

```
history | grep rm
``` filters the list to only show commands containing "rm". 
grep filters on the string "rm".

Then you can offer this information to say cgsecurity forum or other specialists in recovery.

I wonder if you followed some guide on the web and blindly followed the rm command? 
There are some malicious guides out there.

This thread might help you understand what rm can do to an unsuspecting user's filesystem.

[https://askubuntu.com/questions/604324/how-is-rm-rf-able-to-delete-all-files-in-the-system#comment844665_604324](https://askubuntu.com/questions/604324/how-is-rm-rf-able-to-delete-all-files-in-the-system#comment844665_604324)

---

### Post by jgw on 2019-07-10
Thanks for the reply.  

Here is what I did:mnt/05b9fa40-ab8f-4bca-a003-e813169d7e41$ sudo rm -r 05b9fa40-ab8f-4bca-a003-e813169d7e41 (I think I deleted EVERYTHING with the rm command)
'sudo' is where the command starts and it follows where I was when I did it.  

I posted it on cgsecurity.  The reply suggested that I use photorec 7.1  The latest offered by ubuntu is 7.0 so I downloaded the latest and greatest and extracted testdisk-7.1.linux26.tar.bz2   This gave me a folder which usually has directions for installation.  This one doesn't.  I ran into a problem with photorec because it wanted to use my main drive /dev/sda/ to put stuff so I stopped, recorded the entire sequence, explained my ignorance about reinstalling, put the recorded sequence on pastbin ([https://pastebin.com/1YsCkqmt](https://pastebin.com/1YsCkqmt)) and am now currently stopped.  

I have absolutely no idea why I did what I did as it makes no sense at all.  Perhaps I am getting senile.  Its very strange.  I think what I did was delete the uuid with the rm command - didn't even know that was possible!
I just checked again the sequence of this one.  I was dealing with mycroft.  I had found that I had 2 installations and it was messing things up.  I purged it and checked to see if I had anymore mycroft files left.  Found some under that uuid, didn't give it any thought and figured I would just delete that uuid because I was not paying attention and figured it was yet another computer hideyhole.  It was and just happened to be an entire drive.  This, I think, comes under the heading of stupidity and just not paying attention.  I know better but, now, I REALLY know better!

---

### Post by dragonfly41 on 2019-07-11
The version of TestDisk and PhotoRec as held in Ubuntu software centre will always lag the latest version.   In my Ubuntu 16.04 using Synaptic I see that the repo version of testdisk is 7.0-1.   To use the latest version 7.1 this has to be downloaded compiled and installed.

See also 7.1 documentation.

[https://www.cgsecurity.org/testdisk.pdf](https://www.cgsecurity.org/testdisk.pdf)


Start by creating a new folder in your home directory.

```
cd ~
mkdir testdisk-7.1-WIP
```

Now go into that folder

```
cd ~/testdisk-7.1-WIP
```

Now clone the TestDisk source from remote git (read manual 3.3.2).

You will see ..

Cloning into 'testdisk'...

After cloning completed run these commands (you are still in ~/testdisk-7.1-WIP folder)

```
cd testdisk &&
mkdir config &&
autoreconf --install -W all -I config &&
./configure &&
make
```

Now inspect the folder ..
```
~/testdisk-7.1-WIP/testdisk/src
```


Inside amongst many files you will see these compiled executable binaries  ..

photorec
qphotorec
testdisk

You may have your preferred file manager such as Nautilus but I prefer a dual pane file manager .. krusader .. which can be installed ```
sudo apt-get install krusader
```

If I view in Krusader left pane the folder ~/testdisk-7.1-WIP/src/testdisk

and view in right pane the folder /usr/bin

I see the current older versions (7.0) of testdisk and photorec in right pane and the latest version (7.1) of testdisk, photorec, and qphotorec in left pane.

I could overwrite old binaries with new but instead I will simply copy newly compiled qphotorec into /usr/bin

However in trying to copy using Krusader GUI I get an error message 

access denied
Could not write to /usr/bin/qphotorec

This is because I am copying from home folder (/home/username) into /usr/bin/ which requires sudo permissions.

I do this instead in terminal

```
cd ~/testdisk-7.1-WIP/testdisk/src

sudo -H cp qphotorec /usr/bin
```

If in Krusader I now inspect /usr/bin I see that qphotorec is sitting there.

I can now launch this through command line.

```
sudo -H qphotorec
``` .. note the q prefix ..


Bingo.  We have a new GUI for photorec. Version 7.2.


=======================================================

Now you have written ...

> [COLOR=#333333]The problem is that photorec doesn't actually deal with the drive that holds the files /dev/sdc/ but goes to my home directory in /dev/sda/[/COLOR]
[COLOR=#333333]This happens irregardless of my choices (noted in the pastebin file).[/COLOR]

This suggests to me that you may see the devices sda, sdb, sdc .. but are all three mounted?  The source (sdb) and destination (sdc) must both be mounted.

Certainly the OS (/dev/sda) is mounted and running.


I read in pastebin ..

Disk /dev/sdc - 2000 GB / 1863 GiB (RO) - ST320006 44NS

     Partition                  Start        End    Size in sectors
      No partition             0   0  1 243201  80 63 3907029168 [Whole disk]
       > 1 P Linux                    0  32 33 243201  78 13 3907026944 [data-2]



You have not created an internal partition in that new drive which will receive recovered files.

I suggest that you use GParted Partition Editor to inspect /dev/sdc/ and create one or more partitions on that device/drive.  For example you might create a partition named &#8220;data&#8221;
and format that partition as ext4. Again all in GParted Partition editor.

I suggest using half of the drive capacity for your &#8220;data&#8221; partition. 

There are multiple ways of managing mount/unmount partitions.

You can launch Files and in the left panel you can navigate to different partitions and folders.  Right click on partitions and choose mount/unmount.

Another way is using GParted Partition Editor and right click on any partition to mount/unmount.

Yet another way is to run the command findmnt to find mounted partitions (but if they are not mounted you still need to mount them).

Another command is df.

All three drives and internal partitions need to be mounted in order to read recovered files from /dev/sdb and write recovered files into the &#8220;data&#8221; partition in /dev/sdc.

Also in your fresh sdc drive I would create some folders to receive recovered files.

In QPhotoRec there is a checklist where your specify which filetypes you hope to recover.  Try to recall what filetypes you wish to recover? Were they doc files or photos or pdf or txt filetypes for example.

I would select just one filetype for each scan and place recovered files in an appropriate folder. Thus consider running several scans in sequence. This might take much longer but you will not be mixing up different filetypes in one destination folder. Remember that these recovered files will have no filenames and you are still faced with the task of trying to make sense of recovered files.

For example create folders in new &#8220;data&#8221; partition

/doc
/gif
/jpg
/pdf
/png
/sqlite
/ttf
/txt
/zip

---

### Post by oldfred on 2019-07-11
You also may need to give yourself ownership & permissions on your data partition.

       sudo parted -l
sudo mkdir /data
sudo mount /dev/sdc1 /data
#where sdc1 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /data 

Some more tools on sorting & renaming files:
      
 [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html) 
   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by jgw on 2019-07-11
Thanks for the replies.  

My network went down and I have spent the day trying to fix it.  Had to remove the power from the router and leave it off for about 15 minutes before it actually started working.  Then called centurylink and had them check the router, and my lines.  Then  I had ne machine that would not deal with the wired connection but would connect with the wifi (this just goes on and on)

Anyway.  First, 

Disk /dev/sdc - 2000 GB / 1863 GiB (RO) - ST320006 44NS

Partition Start End Size in sectors
No partition 0 0 1 243201 80 63 3907029168 [Whole disk]
> 1 P Linux 0 32 33 243201 78 13 3907026944 [data-2]

sda is my main drive, sdb is the new 2tb drive and both were mounted - sdc Is the drive that I screwed up and was not mounted.  
As I said, I think when I did the rm thing I erased the partition.  The only stuff left that is really left is my backup files (32mb, I think)  

I sometimes use Krisader, not happy with Nautilus but am used to it.

 I decided to use the code boxes for stuff that belonged in pastbin, just thought I would try it.  Now I have to do it all over.  On top of everything else my wife just told me we have guests <sigh>   Interesting times?

I just failed to send a thing that I had been working on to post here with a bunch of stuff but, instead, its gone and I got (more education):
vBulletin Message
Your submission could not be processed because a security token was missing.
If this occurred unexpectedly, please inform the administrator and describe the action you performed before you received this error. If possible, please include the error page URL plus the date and time the error occured.
Tip : Please shorten long posts by using [https://paste.ubuntu.com/](https://paste.ubuntu.com/) for terminal and log output and link to it in your posts.
Ubuntu Forums

I use sudo chown -R name:name  location   to deal with new drives.  this seems to work and gives me back access.  Probably should be root:name but it works.

I have kinda given up on the recovery.  I had the main stuff backed up.  Not as current as they should be but pretty close.  I was worried about our photos and videos but I have made sure my wife's machine was pretty much up to date so I copied those to put on the new drive.  (more than 23000 photos - scanned in every one we had taken before computers, and coverted videos as well.)

Anyway, I really appreciate all the help.  I stil have the messed up drive and plan to have at it again but it seems I am busy with visitors so I get to wait until they leave (haven't been told yet how long they are staying <G>)

Thanks again!

---

