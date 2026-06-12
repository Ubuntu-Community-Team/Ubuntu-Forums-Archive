---
title: "NTFS volumes suddenly empty"
date: 2013-01-31
forum: General Help
---

### Post by wurlyfan on 2013-01-31
Hello

I have just had all data disappear from NTFS volumes on  three internal drives (one new), while working in Ubuntu 12.04, on my  near-new hi-spec'ed Windows 7/Ubuntu box. Everything was fine until I  rebooted the box after installing some software and all the data (about 5  TB) was gone. The partitions are still there, but they show (in Ubuntu  and Windows 7) as completely empty (apart from the System Volume  Information folder). Data in two ext4 volumes, and two connected NTFS USB  drives, was unaffected. On my brand-new 3TB drive, one NTFS volume was unaffected and the other emptied.

I have tried Recuva and NTFS Undelete, but these only show a few old (genuinely deleted) files. Using TestDisk I have confirmed that the files are still there, but named  "inode-xxxxxx". I know I can recover those files these files with Testdisk and  rename them, but that will be a very onerous job (less so for tagged mp3 files, but there are a  large number of video files as well).

I haven't  written anything to the volumes since this happened, and only run the  Windows disk check without the "fix" option. Can anyone suggest another  approach that might recover the file names?

Cheers and thanks for any help.

---

### Post by dino99 on 2013-01-31
testdisk is the best tool as i known; but you also can try to boot on a livecd and run gparted to watch at the partitions, and see if you get it complaining.

are these partitions individuals or some lvm/raid used ?

---

### Post by Mark Phelps on 2013-01-31
> **wurlyfan said:**
> Can anyone suggest another  approach that might recover the file names?

Cheers and thanks for any help.
YES ... the files and directories in the NTFS volumes might be recoverable using RecoverMyFiles from Runtime Software -- an MS Windows app.

You can download and install their trial version for free, run that in deepest discovery mode and see how well it finds the directories and files.  You have to buy it to actually recover the files but at least you get to see if it works, first.

---

### Post by d4m1r on 2013-01-31
What software were you installed and under what OS? Also, what OS did you first boot into when the noticed the data was gone? You have a backup though on an external HDD of course, right?

---

### Post by wurlyfan on 2013-01-31
Many thanks for your replies.

The partitions were all individual, not part of an array. I am running 12.04 precise 64-bit, and was following this post ([http://ossnotebook.blogspot.co.nz/2008/12/how-to-install-boxee-in-ubuntu-64-bit.html](http://ossnotebook.blogspot.co.nz/2008/12/how-to-install-boxee-in-ubuntu-64-bit.html)) to run boxee, by installing 32-bit jaunty alongside the 64-bit OS and using schroot to use it for boxee (I didn't get it to work). I rebooted into Ubuntu (my primary US).

I will look at RecoverMyFiles, although I suspect it won't do any more than Recuva. Gparted shows the partitions as empty, with no problems.

As far as backup in concerned, all my critical data is backed up but if you can suggest a practical and economic way to back up >5TB of video and audio files I'm all ears! Anyway, the data is still there, and it's spread over four physical drives so even with a complete drive failure I wouldn't have lost all of it.

Can anyone explain why only internal drives were affected? I have just moved my several drives  into my box after having had them connected via USB for several years!

Thanks again to everyone.

---

### Post by Mark Phelps on 2013-01-31
> **wurlyfan said:**
> I will look at RecoverMyFiles, although I suspect it won't do any more than Recuva. Gparted shows the partitions as empty, with no problems.

Gparted might be reading the partition indexes, which if they are blank, would look the same as an empty partition.

RecoverMyFiles doesn't both with those indexes but looks for directory and file header blocks.

However, that said, if Recuva found nothing, it's likely that RecoverMyFiles won't find anything either.

They also have another product GetDataBack for NTFS that is not so easy to use but can have better results.  You can also download and install a trial version of that.

---

