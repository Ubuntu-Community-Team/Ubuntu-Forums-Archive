---
title: "NTFS corruption in dual boot after hibernation/suspend"
date: 2013-01-26
forum: General Help
---

### Post by maboventi on 2013-01-26
Hi all,

I'm on a dual boot Ubuntu 12.04/Windows 7 system with an external NTFS drive attached.

After having worked with the external drive in Ubuntu I've booted Windows 7 and I've discovered the last time I've used it was mistakenly suspended/hibernated instead of being shutted down.
When I've rebooted Ubuntu some files were corrupted (ls command says: cannot access <directory>: Input/output error) and one folder disappeared (not even mentioned by the ls command as an error).

My questions are:

1) What tool to use to attempt recovery (better Test-Disk or PhotoRec for this particular situation)?
2) _Most important_ - How can I know if there are other files missing/corrupted in addition to those reported by the ls command as Input/output error?

---

### Post by oldfred on 2013-01-26
If the files were written into the NTFS partition while hibernated, then they are gone as Windows restored the old file structure. Also may be damaged as the hibernated file structure may have had an old version and new version only is partly linked.

I think testdisk will not show the files or folders, either photorec or Windows file recovery tools may find the old files is not already overwritten again. But photorec is a long slow process and only recovers by file type not full file name.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Testdisk & photorec
you want to try some others there are magicrescue ; foremost and scalpel 
Deleted file alternatives this user liked but not free
[http://ubuntuforums.org/showthread.php?t=1339278](http://ubuntuforums.org/showthread.php?t=1339278)
> "GetDataBack for FAT" was the most succesful one among the ones that I've tried. Though it couldn't recover folder's names, it recovered all the files' and sub-folders' name. And it's much better than the others did. Thanks!

---

### Post by puebloan on 2013-01-26
I don't know about you, but it takes me a week to set up a Win7 the way I like it. So, if I were you, I'd dedicate a machine to windows 7 or virtualize it.  Win7 runs pretty good in Virtualbox and it's much much easier to back up that way.

Another advantage to virtualizing your Win7 is that you can stop using it for internet browsing, thereby possibly being able to run without an antivirus, or a least an on-demand scanner. You can keep your Win7 install lean and fast.

It's just not safe to run win7 in a dual boot configuration because your only fallback is a disk image of the entire drive. (IMO)

---

### Post by maboventi on 2013-01-26
Thanks for the given directions!

I've downloaded the demo version of "GetDataBack NTFS" which should be able to tell what and how many files are damaged (the thing I'm interested in most: strangely enough, only very few file seem to be damaged whereas, for what I've understood, all the modifications since the date of hibernation should have been gone).

So, I will try to scan the disk tomorrow with this tool (and maybe with MS chkdisk), then I will post the results.

---

### Post by maboventi on 2013-01-27
Today I've scanned the disk with the demo version of **GetDataBack for NTFS**: missing files are correctly displayed in their original location togheter with all the other files, but in this way the damaged files cannot be distinguished from the others and it's not possibile to know what (and how many) are the corrupted files.

Then I tried **PhotoRec** which started to recover an enormous number of files. In this case too it's too hard to discriminate between corrupted files and regularly deleted ones.

So I made a scan with MS Chkdsk, letting the tool automatically fix filesystem errors (scanning the disk without this option just produced an error message): missing files are properly restored and by reading the log produced it would seem that the only damaged directories are those already reported by the ls command.

It would therefore appear that in these cases the only way to know **what** files are damaged is to actually recover them and then see what files have been recovered. I wonder if, with NTFS filesystems, **fsck** is safe enough to perform recovery when MS Chkdsk is not available.

---

### Post by oldfred on 2013-01-27
There is not a Linux chkdsk. 
The ntfsfix really does very minor fixs and sets the chkdsk flag so when you boot Windows it runs chkdsk.
Some have reported issues with chkdsk but that is the way to repair a Windows file system not necessarily find deleted files. It may even overwrite data in copying it recovered data into chkdsk c:\found folders.

If you have a certain type of file you want to recover you can set that in photorec. It still takes just as long, but only recovers files of the types you check off.

When I used photorec I was primarily recovering some text files that I update daily (my notes I use to post here). My backup was a month or two old. But photorec found every old deleted copy. I had to figure out which files were the same and do many compares. I now at least include the file name in my text files to help in a recovery. Never was sure I found last saved version but got most data back over time.

---

### Post by maboventi on 2013-01-27
Many thanks for the info!

---

