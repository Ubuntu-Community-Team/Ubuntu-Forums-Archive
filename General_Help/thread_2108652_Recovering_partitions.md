---
title: "Recovering partitions"
date: 2013-01-25
forum: General Help
---

### Post by brucecode on 2013-01-25
Hi,

It seems as though I have discovered a flaw with Ubuntu, especially GParted.

I have Windows 7 on a PC with a 120 gig HDD with two partitions. I recently added an identical HDD because I was running out of space on the first. The second drive has previously been used on another PC and I wanted to check to see if there was any data on it I wished to keep. This one also has two partitions but one of them was not accessible under Windows, so I booted into Ubuntu from my live USB.

I could see all of the files on the partition under Ubuntu, so I went back to Windows, realising that it was a permissions problem. I fixed that but decided to resize the two partitions on the second drive to free up space. This took ages so I thought I'd try to see if Linux was any quicker at the job, so I booted back into Ubuntu.

The resize under Windows had only been to reduce the size of the first partition. Under Linux I increased the size of the second partition and copied all files from the now smaller first partition to the larger second partition. I rebooted the computer but got an error message saying that the computer could find a system disk. I ran Windows Recovery from the DVD and was told that there was no system partition.

Knowing that I hadn't touched the first drive I booted back into Linux to find out what was wrong - maybe a drive had a flag changed or something.

When I got into Ubuntu I found that somehow Ubuntu had decided that the two drives were a mirrored set and had completely overwritten the first drive, which was my Windows drive.

I've now got nothing. Can anyone tell me how to recover my partitions from the first disk? Can anyone also tell me why Ubuntu decided that both drives should be a mirrored pair? I did NOTHING with the first drive. I didn't mount it, I didn't view it, I did nothing.

I have some Windows software for partition recovery but I suspect that it won't be any use since there now appears to be two fully working partitions on the drive - they just aren't the two I had in the first place.

Any help in restoring my sanity or placating me would be appreciated.

Thanks,

Bruce

---

### Post by oldfred on 2013-01-25
Welcome to the forums.

Never heard of that except where a user copied the partition from one drive to another. Unless drives were RAID from BIOS and configured as RAID I do not see how that could automatically occur.

If you overwrote data onto Windows partition you may not have much to recover, and it will not be bootable as any system file overwritten would prevent it from working. But you may be able to recover some data. 

Testdisk may find old partition structure and may show files if file table still there. 
If testdisk does not work then there is photorec. I have used photorec, it is a long process, only recovers files by type or extension not full filename and you need another drive with room to copy data onto.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

    
       repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

            Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by brucecode on 2013-01-28
Hi oldfred,

Thanks for your reply. Thankfully I had a bunch of goes at testdisk because, while it found nothing the first few goes, I have finally been able to recover one of the two overwritten partitions. I have no idea why nothing was found the first few times but now has been found, but I'm not complaining! At least I have a backup of the second partition and the files from the first have been restored to an external drive.

My next step in restoring my system is to find out how to break the RAID. I have moved the drives from ports 0 and 1 on my motherboard to ports 0 and 5 and have ensured that RAID was not set in the BIOS (it was enabled in the BIOS but had not been set up - it is now totally disabled) but there is still a device called /dev/mapper/xxxxxxxx which, I understand, is a RAID setup?

Ubuntu (GPart rather) won't allow me to manipulate the drives independantly, so I assume that I need to break the RAID set first so that I can repartition these drives and restore my data.

For what it's worth, I still don't know how Linux assumed that the drives were in a RAID, let alone mirrored. Windows saw the drives as individuals and I gather that Linux was happy to let me go along with that until I tried to resize the partitions and then Linux 'chose' to enforce what it saw as a mirrored array.

Thanks,

Bruce

Edit: I've now tried to boot from two different Ubuntu Live USBs - the first is 12.04 with persistance, the second is 10.xx without persistance. The second was booted after I had totally disabled the RAID controller in the BIOS but it still sees /dev/mapper ...

---

### Post by ronparent on 2013-01-28
You apparently got your hands on a disk with raid metadata. If so, it is persistent and has to be erased to be able to use the drive normally. Open a terminal and write: > sudo dmraid -Ea /dev/sdb assuming sdb is the new drive. Actually it wouldn't hurt to run the command for each drive.

With the raid metadata erased the /dev/mapper symbolic links should disappear after the next boot.

---

### Post by oldfred on 2013-01-28
If you do not want RAID you have to run the command ronparent suggested to remove meta-data from drive. Gparted will not work on a drive that is RAID, as you have to use RAID tools to edit RAID partitions.

Did you turn RAID on in BIOS or in Windows turn on Intel SRT as that uses RAID?

---

### Post by brucecode on 2013-01-28
Hi ronparent and oldfred,

ronparent, when I run that command verbatim in a terminal, I get a message to the effect that 'ERROR: invalid option argument for -a', yet I definitely type '-Ea'. I tried this on both sda and sdc and got the same result for both.

oldfred, I've never had RAID turned on in the BIOS for this machine. I almost definitely *did* have it turned on for both of those drives in a different, non-Linux machine in the past though. Oddly, both Windows 7, when it was working, and the Windows 7 DVD used for recovery see the drives as seperate entities.

Since the dmraid command did not work is my only option now to fully delete all partitons and data and start again? I would guess that if the previous drive metadata is the issue, then this will still effect the drives if I repartition? Last night I did use the Windows 7 DVD to delete the second partition on the first drive and extend the first partition. Ubuntu shows these changes for the drive /dev/sda but not for /dev/mapper - as expected I guess considering what you've said above about GParted.

Thanks,

Bruce

---

### Post by oldfred on 2013-01-28
You may have to install the dmraid driver first.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by ronparent on 2013-01-28
brucecode - the commands oldfred gives above are correct - my memory was faulty. The raid bios doesn't have to be turned on for drives to be recognized as raid, simply the presence of the metadata will do it. Erasing the metadata will fix that problem. If your not intending to use fakeRAID, further uninstalling dmraid after deleting any metadata would not hurt and should clean up your system.

---

### Post by brucecode on 2013-02-05
Hi,

Thanks for your help oldfred and ronparent. I'm marking this thread as solved. I've recovered most of my data (all the important stuff anyway) between backups and partition recovery and have removed RAID metadata. I have noticed that almost all largish files (over a couple of meg) are corrupted, but that isn't too much of a problem, just a note for curiosity.

I would recommend any other people reading this thread for help to follow the instructions in reverse:


[LIST=1]
[*]**Check BIOS for RAID and turn it off** if you don't wish to use it. Even if you don't have RAID set up but it is on in the BIOS, probably still turn it off.
[*][B]Remove RAID metadata by running the command 
*sudo dmraid -E -r /dev/sd(X)*
[/B] on each drive you do not want to be part of RAID where **/dev/sd(X)** is your hard drive e.g. mine were /dev/sda and /dev/sdc.
[*]**Run testdisk** to recover files and, I would suggest, ensure that files are firstly saved to an *entirely different* drive. It isn't too hard to copy your recovered files back to your original intended device once you are sure you have all you can save, but each time you write to your drive (i.e. if you recover directly to your drive) you reduce your chances of successfully recovering more data.
[/LIST]
As mentioned most (more than half) of my files over 2 meg are corrupted and I could never recover *anything* from the second overwritten partition, but I have backups of that.


Thanks again,


Bruce

---

