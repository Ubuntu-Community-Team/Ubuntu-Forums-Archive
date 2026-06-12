---
title: "Clonezilla problem"
date: 2013-03-05
forum: General Help
---

### Post by nickdc on 2013-03-05
I've just attempted to clone an NFTS partition containing Windows XP (prior to wiping it altogether) using Clonezilla (very recently downloaded live cd, so latest stable version). The partition has about 150gb of data and it was being saved as an image on an external usb drive (Seagate FreeAgent). According to Gparted the latter is formatted ext4 and has about 750gb unused space on it, confirmed also by the file browser in Ubuntu (which is on another partition on the same disk as XP - ie a dual boot setup). The cloning process started fine, but after a short while it terminated, saying there was insufficient space on the target drive. I don't understand this and would be grateful for advice from more experienced users. Should I suspect Clonezilla (it has a very good reputation), the FreeAgent drive, or something else? Are there ways of probing the external drive to find out more of what's going on? :confused:

---

### Post by Mark Phelps on 2013-03-05
Is Windows XP working? If so, what I would recommend, instead of Clonezilla (which I use all the time to backoff Linux filesystems), is to download and install the Free version of Macrium Reflect in XP, and use that to image off XP to an external drive.

---

### Post by nickdc on 2013-03-06
Thanks for that suggestion, Mark. I've not come across Macrium Reflect, so will check it out. I've already got Ghost (early version before it got messed up) but I've learned to be wary of using Windows to clone Windows. A lot of people suggest Linux handles such things much better. But before I go any further I really want to investigate the FreeAgent drive, as I don't want to be using it to store important backups if there are issues with it.

---

### Post by mastablasta on 2013-03-06
you can try redobackup.

perhaps you didnt' set clonezila propperly. their menues can be confusing sometimes.

---

### Post by nickdc on 2013-03-06
I've had another try, this time saving the image to a folder, rather than root, in the external disk (vaguely remember reading something yonks ago about not saving directly to root in these drives), but the same thing happened: "the device is full. Create more disk space and try again!" Or words to that effect. I've had a look at Macrium Reflect, but can't find any info about supported file systems. Most Windows programmes can't write to Ext4, so without confirmation that it can, I'm reluctant to use it. I suppose I need to try with another drive, but I don't have a suitable one to hand at the moment. I can't reformat the one I've been attempting to use as it has other important data on it. Anyone got any bright ideas?

---

### Post by mike555 on 2013-03-06
Check the external drive for hidden files ,like .trash , perhaps that is filling it up.

---

### Post by nickdc on 2013-03-08
Thanks. There's only the one hidden file, .trash and that has very little in it. In the meantime I've found another drive and will be using that for the cloning. I should have space on it to take all the stuff on the problem drive too, then I'll reformat it and see if that helps.

---

### Post by ibjsb4 on 2013-03-08
I would do it a bit different.  Instead of a snapshot I would clone partition to partition and for windows I would use NTFS filesystem.  Forget exactly how its worded, but would also just use the easy (beginner?) clone.  Your USB HDD being empty, clonezilla will use the whole thing.  Just a suggestion as this works for me.

---

### Post by cmcanulty on 2013-03-08
I believe when you clone it copies empty and full sectors so you need a hard drive at least as big as one you are cloning even if it is mostly empty

---

### Post by nickdc on 2013-03-08
Thanks for those helpful suggestions. I've made a start now, using Redo. So far so good - none of the problems I had before - but it's got another 3 hours to go. If successful I'll review the strategy, but for the moment after a whole run of things not going right it's just great to have something going to plan!

---

### Post by sammiev on 2013-03-08
I use Clonezilla all the time ( weekly ) to backup my full HD with 4 OS and it takes about 30 min to do so. If I do a full restore once again 30 min and I'm back to what I had when I backuped. Likely you are having troubles with the menu in Clonezilla. I also backup to a Seagate FreeAgent.

---

### Post by Manyette on 2013-03-08
Just as an FYI, I've been using Clonezilla for several years, and have never had a problem.  I also use Seagate USB3 Freeagent as my backup and it has never failed me.  And I use it Clonezilla because it is a true baremetal backup which I depend on.

---

### Post by nickdc on 2013-03-09
Thanks for the last two comments. Redo has been successful, but taking nearly seven hours to clone two Windows partitions of about 250gb in total is hardly quick. On the other hand, it worked. Maybe Clonezilla would with the different drive. I might just have a try, just to compare speed.

While I've had lots of helpful advice re cloning, there's been hardly any response to my request as to how to proceed in troubleshooting the FreeAgent drive. It's an older model, and I'm sure it didn't come with ext4 on it, so at some stage I must have reformatted it, but it's not given any trouble for simply copying files and folders for manual backup. If Clonezilla works ok with the alternative drive, that suggests the OP problem *is* with the FreeAgent, especially as Redo couldn't succeed with it either ("write error -1"), though I only tried the once.

---

### Post by nickdc on 2013-03-09
> **cmcanulty said:**
> I believe when you clone it copies empty and full sectors so you need a hard drive at least as big as one you are cloning even if it is mostly empty

Well for info, now I've had success with Redo it seems to have just cloned the data areas, not the empty ones, and it's compressed them a little. The two partitions I've cloned have a combined size of 190gb, containing just over 150gb of data, but the backup file of the lot is 125gb. That's using the "create image" option, though. Perhaps if I'd cloned "partition to partition" it would have "copied" the empty areas too.

---

### Post by sudodus on 2013-03-09
> **nickdc said:**
> Thanks for the last two comments. Redo has been successful, but taking nearly seven hours to clone two Windows partitions of about 250gb in total is hardly quick. On the other hand, it worked. Maybe Clonezilla would with the different drive. I might just have a try, just to compare speed.

While I've had lots of helpful advice re cloning, there's been hardly any response to my request as to how to proceed in troubleshooting the FreeAgent drive. It's an older model, and I'm sure it didn't come with ext4 on it, so at some stage I must have reformatted it, but it's not given any trouble for simply copying files and folders for manual backup. If Clonezilla works ok with the alternative drive, that suggests the OP problem *is* with the FreeAgent, especially as Redo couldn't succeed with it either ("write error -1"), though I only tried the once.

I have good experiences with Clonezilla writing images to linux ext file  systems. I don't think it is a problem with the size of partition, but  something else.

A couple of tips to find out why Clonezilla won't work for you:

1. Did you notice if there was something written on the drive at all after Clonezilla stopped? Could it be a problem with identifying the drive and partition? I know that sometimes Clonezilla and Ubuntu will detect drives in different order (for example sdc will be one drive in Ubuntu and another one in Clonezilla). If this was the case, maybe you were trying to write to a USB pendrive or some other drive with a too small partition.

So please double-check that it is the correct drive and partition, that you mount as target (where the image is to be written).

2. Maybe there is something with the FreeAgent, that cannot be managed by Clonezilla. This might be checked with the following method.

Instead of running Clonezilla's wizard system 'Start Clonezilla', you can 'Enter_shell' and run some commands to check that the drive and the partition you want to use are properly recognized.
```
sudo blkid
```
```
sudo fdisk -lu
```
and when you identify the partition [FONT=courier new]**/dev/sdxy**[/FONT] try to mount it (x is the drive letter and y is the partition number)
```
sudo mount -t auto /dev/sdxy /mnt
```
and see how much space is reported
```
df -h
``` and check how it is mounted with
```
cat /etc/mtab
```

---

### Post by sudodus on 2013-03-09
> **nickdc said:**
> Well for info, now I've had success with Redo it seems to have just cloned the data areas, not the empty ones, and it's compressed them a little. The two partitions I've cloned have a combined size of 190gb, containing just over 150gb of data, but the backup file of the lot is 125gb. That's using the "create image" option, though. Perhaps if I'd cloned "partition to partition" it would have "copied" the empty areas too.
It looks good. I think you have succeeded with Redo. [COLOR=#808080]If you want to be 100% sure, you need to restore the image, but not overwriting the original partitions, so you need an extra drive for that purpose.[/COLOR]

I have not used Redo, but normally such programs copy only blocks containing data. But 'partition to partition' should mean cloning so that the target partition with contain the same data and free blocks at the same places as the source (but the free blocks will contain different data unless both were zeroised before the cloning). Such operations can only be done if the target partition is at least as big as the source (and if different sizes, the file system will need to be checked and fixed afterwards).

---

### Post by cmcanulty on 2013-03-09
I have had a lot of problems previously with external drives mounting. Here are some things that worked for me 1)make sure it isn't in fstab unless you want it always mounted at boot. 2) run this script and try again


```
sudo killall udisks
```

```
sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall

```

---

### Post by Mark Phelps on 2013-03-09
One not so obvious "problem" using Clonezilla, that takes some getting use to, is that unlike with MS Windows imaging apps, in Clonezilla, you have to specify the DESTINATION first, not the SOURCE.  This confusion can generate error giving the impression that it won't work, when in fact, you just have to reverse the usually order of specifying source and destination.

---

### Post by nickdc on 2013-03-10
> **sudodus said:**
> I have good experiences with Clonezilla writing images to linux ext file  systems. I don't think it is a problem with the size of partition, but  something else.

A couple of tips to find out why Clonezilla won't work for you:

1. Did you notice if there was something written on the drive at all after Clonezilla stopped? Could it be a problem with identifying the drive and partition? I know that sometimes Clonezilla and Ubuntu will detect drives in different order (for example sdc will be one drive in Ubuntu and another one in Clonezilla). If this was the case, maybe you were trying to write to a USB pendrive or some other drive with a too small partition.



Yes, there were a lot of files, clearly the cloning had got well underway. And it was definitely writing to the correct drive; I checked that very carefully before starting it off. 
Thanks very much for posting the code to use to investigate further. I haven't yet had time, but I'll definitely try that.

---

### Post by nickdc on 2013-03-10
"I have had a lot of problems previously with external drives mounting.  Here are some things that worked for me 1)make sure it isn't in fstab  unless you want it always mounted at boot. 2) run this script and try  again" [Can't get quotes to work properly atm]

Thanks for this; I think you may be on to something. I had noticed that not only does the FreeAgent drive mount at startup, it also opens a window on the desktop. I was very surprised at this, as my partner leaves everything to me - she wouldn't have known how to get it to do that, and I've never set it to do that. Following your post I've now checked fstab, and there's nothing there referring to that drive. It's just dawned on me what may be happening:  there's a powersaving plug that fires up/down all the peripherals a few seconds after switching on/off the pc. I think the timing is such that the FreeAgent powers up just as the OS finishes booting, so it is mounted and opens a window just as it would if hot plugged at any time while the OS is running, but it *appears* to be auto-mounted on startup. Does this make sense, and could it account for the Clonezilla problem? I have other things to deal with atm, but will try using the code you posted. Many thanks.

---

### Post by sudodus on 2013-03-10
> **nickdc said:**
> "I have had a lot of problems previously with external drives mounting.  Here are some things that worked for me 1)make sure it isn't in fstab  unless you want it always mounted at boot. 2) run this script and try  again" [Can't get quotes to work properly atm]

Thanks for this; I think you may be on to something. I had noticed that not only does the FreeAgent drive mount at startup, it also opens a window on the desktop. I was very surprised at this, as my partner leaves everything to me - she wouldn't have known how to get it to do that, and I've never set it to do that. Following your post I've now checked fstab, and there's nothing there referring to that drive. It's just dawned on me what may be happening:  there's a powersaving plug that fires up/down all the peripherals a few seconds after switching on/off the pc. I think the timing is such that the FreeAgent powers up just as the OS finishes booting, so it is mounted and opens a window just as it would if hot plugged at any time while the OS is running, but it *appears* to be auto-mounted on startup. Does this make sense, and could it account for the Clonezilla problem? I have other things to deal with atm, but will try using the code you posted. Many thanks.

This might or might not be a problem. Where is that powersaving plug installed? And how are you running Clonezilla (from a clonezilla boot CD or have you installed Clonezilla into her present system)? Could the powersaving plug run when you are running Clonezilla?

---

### Post by nickdc on 2013-03-10
> **sudodus said:**
> This might or might not be a problem. Where is that powersaving plug installed? And how are you running Clonezilla (from a clonezilla boot CD or have you installed Clonezilla into her present system)? Could the powersaving plug run when you are running Clonezilla?

The powersaving plug is in the mains wall socket; it's like a three-way adapter but with internal electronics, so you plug your pc mains lead into the 'master' socket and peripherals into the other two. It detects when you switch the pc on or off and delays/maintains power to the two peripherals sockets for about 5 seconds after. The powersaving comes from ensuring all peripherals power down once the pc is off; it doesn't do anything while the pc is running apart from supplying juice. I'm running Clonezilla from a live cd.

---

### Post by sudodus on 2013-03-10
> **nickdc said:**
> The powersaving plug is in the mains wall socket; it's like a three-way adapter but with internal electronics, so you plug your pc mains lead into the 'master' socket and peripherals into the other two. It detects when you switch the pc on or off and delays/maintains power to the two peripherals sockets for about 5 seconds after. The powersaving comes from ensuring all peripherals power down once the pc is off; it doesn't do anything while the pc is running apart from supplying juice. I'm running Clonezilla from a live cd.

I see, so if you ***reboot*** to start Clonezilla (not poweroff and poweron), the powersaving plug should not interfere with the external drive. Of course you can try Clonezilla again using reboot, but on the other hand, if you are happy with Redo, that's fine, and you need not troubleshoot Clonezilla.

---

### Post by nickdc on 2013-03-11
> **cmcanulty said:**
> I have had a lot of problems previously with external drives mounting. Here are some things that worked for me 1)make sure it isn't in fstab unless you want it always mounted at boot. 2) run this script and try again


```
sudo killall udisks
```

```
sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall

```

I've just tried running that script and gone down at the first hurdle: "sudo killall udisks"  returns "udisks: no process found"   I don't know what to make of this.

For information, the FreeAgent drive was running and mounted while I ran that code and it is connected with a usb cable, via a usb hub. The pc is running Ubuntu 10.04LTS, not the latest version (I thought I'd mentioned that in my OP, but checking back I can't find it - apologies.)

---

### Post by cmcanulty on 2013-03-11
try both scripts without the drive mounted. I usually get the no process found on 1st command and then still run the second script.Then try mounting disk

---

### Post by nickdc on 2013-03-11
Thanks for such a quick reply! When you say "Then try mounting the disk", do you mean with Clonezilla? Ie run the scripts, then reboot to Clonezilla cd and try the cloning again? Also, presumably the drive should stay on and connected while I run the script, but unmounted by Ubuntu? I just wanted to make sure!

---

### Post by cmcanulty on 2013-03-11
No I mean remove the ext drive, run both scripts then try mounting the disk, then try clonezilla. Worth a try and won't hurt anything

---

### Post by nickdc on 2013-03-11
> **cmcanulty said:**
> No I mean remove the ext drive, run both scripts then try mounting the disk, then try clonezilla. Worth a try and won't hurt anything

Thanks. OK, I've done that now, but it's terminated again with the same problem. This time I took a note of what was on the screen. Also, though I didn't note it down, I noticed some info which might be relevant when Clonezilla started off. There were a couple of lines about modprobe and failing to find certain modules, also a line about kernel frequency which had a red [fail] where other lines had an [OK]. However, it did the same with the successful clone to the other (extSATA) drive the other day, and on both occasions it has continued to start creating the image, completing the first, much smaller partition, without a problem. But about a third to half way through the big one it terminated. I wasn't there watching it, but on the screen when I returned were 25 lines like this:
[8182.**576010**] Buffer I/O error on device sdc1, {*that's the FreeAgent*} logical block **41744359**  {the numbers I've put in bold changing incrementally each line}

then

[8182.634402] journal commit I/O error split: /home/partimage/2013-03-11-17-imageXPpartitions/sda2.ntfs-ptcl-img.gz.be: Input/output error
                 Checking the disk space ....
[8183.453144] EXT4-fs error (device sdc1) : ext4_find_entry:1209: inode #2 : Comm dd: reading directory lblock 0 
/home/partimage is full! No space left on device!

Then telling me to create more space and try again.

Actually checking the FreeAgent (sdc1) I find the folder for imageXPpartitions, containing 40 items totalling 62.7 gb. The drive as a whole (which has other backup stuff on it) shows as having 234.4gb used and 682.5gb free! And just to add: when this happened the first time, just in case the other stuff on the drive was causing a problem, I made a separate partition on the drive, just to take the Clonezilla image, but I got the same aborted process. I've since deleted that partition and put the drive back as it was.

Does any of the above provide clues as to what is going on?

---

### Post by cmcanulty on 2013-03-11
I would try another cloning app. I often have even windows 7 imaging fail. Some software is more fault tolerant than others. For example if you have one iffy file you still want to clone and can live with an iffy file or one file that fails. 
[http://lifehacker.com/5891933/the-best-disk-cloning-app-for-linux]("http://lifehacker.com/5891933/the-best-disk-cloning-app-for-linux")
[http://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/]("http://www.makeuseof.com/tag/2-methods-to-clone-your-linux-hard-drive/")

---

