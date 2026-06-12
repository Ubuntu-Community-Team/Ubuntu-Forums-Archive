---
title: "My SDD is not booting anymore - Unable to access"
date: 2020-09-19
forum: General Help
---

### Post by xfaraway00 on 2020-09-19
Hello, 


I have a NUC with 1TB SDD, where I have been running Ubuntu successfully for a while. Suddenly, when I tried to start the device, a message appeared: Not a bootable device found. I entered the BIOS of the NUC, and could not find the Hard Drive.


Then I proceed to start the NUC with a bootable USB with Ubuntu. And the hard drive is there /dev/sda. However, the partition is not recognized. 


I extracted the SSD and connected to a USB box to try to plug the hard drive to another PC running windows. Using DiskInternal Linux Recovery, I get the same: There is a hard drive with an unknown partition. 


I am quite worried since I have important information in this hard drive and not a Backup. Literally, I was going to run the backup when I turned it on.


Is it possible that the Hard Drive is encrypted, and that is why the partition is not detected? If this is the case: I should know the Paraphrase. But I have no idea how to recover the access.


I will much appreciate your help!

---

### Post by oldfred on 2020-09-19
If the UEFI/BIOS cannot see the drive, then no Linux tools will be able to do anything.

Check cables, connections, but may be drive failure?

---

### Post by xfaraway00 on 2020-09-20
The drive can be seen. But it says that is missing super block.

---

### Post by dinkidonk on 2020-09-20
Sounds like the partition table or file system has become corrupt, this usually happens if the drive suddenly looses power (bad cable, power outage etc.) or if it is (becoming) faulty. You should try to make an image of the drive with ddrescue, when the drive is properly backed up you can continue to try to fix the broken partition table and/or file system with TestDisk. If the drive is not recoverable, you can use a file carver like PhotoRec (part of TestDisk) and see what may be salvageable. Good luck!

---

### Post by TheFu on 2020-09-20
There are 1001 reasons to have daily, automatic, versioned, backups.
Computers don't care about our plans to backup.

For something like this, you will be spending a bunch of time recovering files with useless names, then hours, days, weeks, trying to put the names to the files.  I know.  I've been where you are. TestDisk is the tool of last resort for this reason. For my sneaker*net storage devices, every few months, I fill the empty space on those drives with zeros so really old data that I will never need again doesn't get "found" when using testdisk.

A quick search found this: [https://ubuntuforums.org/showthread.php?t=1245536](https://ubuntuforums.org/showthread.php?t=1245536) Before attempting any data recovery, you'll need 2 more storage devices.  
[LIST]
[*]a. for the recovered data
[*]b. for the cloned disk image, so you can't do any more harm to the data then has already happened. I'd use **ddrescue** to clone the disk at the disk level (sdZ), not the partition level (sdZ1).
[/LIST]
I'm a believer that whenever people don't follow the 2-disk model above, then they will also hurry and destroy all the data they hope to recover.  I've been there. Most of us have.

Being able to restore data from backups is 10-1000x easier than anything you are going to attempt. Good luck. 

Get backup religion ASAP.

---

### Post by xfaraway00 on 2020-09-20
Test Disk on Windows was unable to find anything.

---

### Post by CelticWarrior on 2020-09-20
So the conclusion is the drive is faulty.

---

### Post by MartyBuntu on 2020-09-20
> **TheFu said:**
> 

For something like this, you will be spending a bunch of time recovering files with useless names, then hours, days, weeks, trying to put the names to the files.

Being able to restore data from backups is 10-1000x easier than anything you are going to attempt. Good luck. 



I used Test Disk on my daughter's files on an XP machine, back in 2006, that was never regularly backed up.
Test Disk is something I wouldn't wish on an enemy.

I've used Acronis since 2005 and more recently TeraByte. Storage is cheap....time spent on possible recovery is not.

---

### Post by xfaraway00 on 2020-09-24
Hello everyone. 

Just an update: The drive was damaged. 

I took the disk to a Recovery Data service and they found out there is a severe failure on the printed PCB. They will have to re-program the main modules of the information scanner device, locate the lost and corrupted channels and ports of the volume.

---

### Post by rbmorse on 2020-09-24
Maybe it's my abject ignorance, which I freely acknowledge, but something about that doesn't sound right.

---

### Post by Autodave on 2020-09-24
Whenever you see "super block not found", you have a 99.9% chance that the drive has failed.

---

### Post by oldfred on 2020-09-24
While often not recoverable, there are back up superblocks.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by TheFu on 2020-09-24
> **xfaraway00 said:**
> Hello everyone. 

Just an update: The drive was damaged. 

I took the disk to a Recovery Data service and they found out there is a severe failure on the printed PCB. They will have to re-program the main modules of the information scanner device, locate the lost and corrupted channels and ports of the volume.

Did you get a 2nd opinion?  If you were going in for heart surgery, wouldn't you get a 2nd opinion?

I wouldn't trust Windows tools to recover non-Windows data, unless it was purely block-level stuff that doesn't care about files, file systems, partitions.

Hopefully, you'll get daily, automatic, backup religion from this experience. With good versioned backups, stuff like this is an inconvenience, not data loss.

---

### Post by HermanAB on 2020-09-25
I am surprised that the Recovery Service doesn't need to reconfigure the nurgle and change the polarity of the forward deflector array also.

As suggested above, you should probably get a second opinion.

---

### Post by xfaraway00 on 2020-09-25
I did not get a second opinion yet. I dont think where I am, there is many services that do that.... I went also to one with "good reputation", as the data has some type of value. So probably I am paying a premium for it.

Definetely will be more methodic about backups. I usually do them but this time, and this drive I did not do it!

---

### Post by HermanAB on 2020-09-25
I'm sure this will not cheer you up at all, but I have never been able to recover data from a failed SSD.  They all suffered a sudden death and that was it. Now you see it, now you don't.

---

### Post by dinkidonk on 2020-09-25
Most SSD's use internal encryption with a key stored on the drive, if the PCB (controller) fails then the recovery of that key is either impossible or extremely time consuming. Without the key, data recovery is impossible.

---

### Post by xfaraway00 on 2020-10-05
Update: Apparently they are having a hard time to recover any data from it due to the SSD's failure. 

Any suggestions before discard the drive? 

Perhaps the manufacturer? 

Thx

---

### Post by dinkidonk on 2020-10-05
> **xfaraway00 said:**
> Any suggestions before discard the drive?

As mentioned in my previous post, data recovery from SSD's is tough and most likely impossible. Backing up the data before it is necessary is easy, though.

---

### Post by xfaraway00 on 2020-10-06
Their final diagnostic is:

[B][I]The NAND flash memory chip shows irreversible damaged cells that prevent the correct data recovery.
[/I][/B]
Does anyone recommend another company/service I could send the SSD to? before discard it 100%

---

### Post by dragonfly41 on 2020-10-06
I have learned from this thread that I must be careful in understanding SSD failure (I have two in use).
I searched locally in the U.K. and found [one service here]("http://www.datarecoveryspecialists.co.uk/") which I have not used but they seem to be experienced.
At least get a second opinion and ask how they might recover from such a scenario.
The advice on backup should now be seared into us.

---

### Post by xfaraway00 on 2020-10-06
Thank you.

Honestly, I run backups always. Specially for the type of the files I am missing, I usually keep 2-3 copies.

But this time, I had this file without backup temporarily in this drive. Literally, I was in the middle of cleaning some data from other computer, and I dumped this data in a new file on a new drive just temporarily with the intention to put it back in the original file with its copies. Thus,..., the temporarily drive failed, in a matter of a week of use! 

I dont want to even think about it in depth because otherwise, it will drive me crazy. I just want to get over this... The loss of this file, will imply an economic loss.

Im now trying to talk to the people that checked the drive, and see if ALL of the NAND chipsets are damaged, or there is the posibility to scope some, or what would be another possible solution... 

Thank you all... and yes, backup all. even the backup

---

### Post by dragonfly41 on 2020-10-06
> [COLOR=#000000]Im now trying to talk to the people that checked the drive, and see if ALL of the NAND chipsets are damaged, or there is the posibility to scope some, or what would be another possible solution...

[/COLOR]I do suggest at least talking to the company I linked to.

[http://www.datarecoveryspecialists.co.uk/services/ssd-recovery](http://www.datarecoveryspecialists.co.uk/services/ssd-recovery)

Do not put all your eggs in one basket. Consider multiple sources of advice. They will often conflict.

---

### Post by dinkidonk on 2020-10-06
If the NAND chips are damaged, the drive is toast.

---

### Post by xfaraway00 on 2020-10-06
> **dragonfly41 said:**
> [/COLOR]I do suggest at least talking to the company I linked to.

[http://www.datarecoveryspecialists.co.uk/services/ssd-recovery](http://www.datarecoveryspecialists.co.uk/services/ssd-recovery)

Do not put all your eggs in one basket. Consider multiple sources of advice. They will often conflict.

Actually I spoke with them, and they say that when NAND chipsets are damaged, not necessarily ALL of the cells are damaged. So they might be able to recover some files from it.

On the other hand, I just spoke with the people that are looking at the drive now, and they did not inspect the hardware. They were just working on the cloned image. - That is what I was doing too...

---

### Post by xfaraway00 on 2020-10-06
> **dinkidonk said:**
> If the NAND chips are damaged, the drive is toast.

Question regarding this. IF the NAND chips are partially damaged, is there any chance to recover data from the parts that are not damaged?

I am having the hope that these guys did not even look at it closely, and just ran some basic tools.

---

### Post by dragonfly41 on 2020-10-06
I wrote earlier ..
[COLOR=#000000]
"Consider multiple sources of advice. They will often conflict."

That is proving to be the case.[/COLOR]

---

### Post by xfaraway00 on 2020-10-06
Definitely - thank you.

It seems that what I am looking at is a Chip-Off data recovery. 

I will keep you posted. 

Regardless the outcome, which I hope is positive, it seems an interesting and common problem, so this would be a good thread for future users with bad luck and/or acting unresponsively by not doing regular backups of everything.

---

### Post by dinkidonk on 2020-10-06
If the drive uses internal encryption, some damaged cells may result in an "avalance effect" that causes a larger area to be garbled. It MAY be possible to recover SOME data, but I would not keep my hopes up. Chip damage usually happens in the cells often written to, which means whatever you where working on. System files which are rarely, if ever, written to are less prone to cause chip damage.

I would like to know what type of drive it is and if it was damaged by a power surge / transient or sudden power loss or if it just happened during normal operation? Was the drive full or was there enough free space for over-provisioning?

---

### Post by xfaraway00 on 2020-10-06
If the drive uses internal encryption, some damaged cells may result in an "avalance effect" that causes a larger area to be garbled. It MAY be possible to recover SOME data, but I would not keep my hopes up. Chip damage usually happens in the cells often written to, which means whatever you where working on. System files which are rarely, if ever, written to are less prone to cause chip damage.

> **dinkidonk said:**
> I would like to know what type of drive it is and if it was damaged by a power surge / transient or sudden power loss or if it just happened during normal operation? Was the drive full or was there enough free space for over-provisioning?

It is an Inland 1TB SSD that I bought at Microcenter (Massachusetts). Not the best quality I guess.

So the drive was not full at all. Actually I assume it was fairly empty. The file I am trying to recover is about 100-200K.

I did not noticed when it failed. It wasnt during normal operation. Perhaps a sudden power loss. I just noticed the failure when I turned it on after some weeks of inactivity.

---

### Post by dragonfly41 on 2020-10-06
> [COLOR=#000000]The file I am trying to recover is about 100-200K.

Have you ever had this file on another drive and then deleted after copying to your SSD?
If so, then there is a slim chance that you might recover it as a deleted file on the other drive.[/COLOR]

---

### Post by xfaraway00 on 2020-10-06
Nope. it was created in this drive. And literally, was about to extract it when I turned the computer on.

---

### Post by xfaraway00 on 2020-10-07
Alright,

**Update:** The drive has no mechanical/hardware issues. It is a problem with the firmware of the drive that failed. 

**The data is there and recoverable. **

---

