---
title: "Recover Lost Partition"
date: 2015-07-18
forum: General Help
---

### Post by V_Narayanan on 2015-07-18
Hi
I used to promote use of Linux as an average end user to reduce costs and also save machine.
I had so far successfully installed Ubuntu side by side Windows

However, two days before when I attempted to install Ubuntu side by side windows, I found that the option was no more available
So I used the Option "Install in the lonest free space available".
It resulted in using of the entire Hard Disk, my friend felt very bad and has not taken back-up

So I used a liveboot and installed testdisk & ddrescue-gui and scanned his hard disk
Testdisk pointed out the partitions before installation of ubuntu but failed to show any files
ddrescue created some unique files in the hard disk and also made the entire hard disk as "Lost Partition"
In addition ddrescue has also made my External Harddisk useless by removing 915GB out a TB.

Testdisk did not even showed the partition table before the ddrescue creating the useless files
ddrescue is not usable as I do not have back-up device

fcsk -l is not usable as -l option is not available

gpart scan is being run now
I do not know, whether it would help

I am really helpless and do not know what to do.
Yours
VN

---

### Post by oldfred on 2015-07-19
Anytime you make a major system change you need to update backups.
And hard drives fail, I even had a new one fail within a year, so backups should always be ongoing.
And backup applies whether Linux or Windows or any system.

dd is a size for size copy from one device to another, and totally overwrites without any warning to the other device. If you had any data on device you copied to, it is gone. That is why dd's nickname is "Data Destroyer". You should have only used ddrescue to copy to a blank device.

Best case is that deeper search in testdisk finds files. But if not you can use photorec which just scans drive for anything that looks like a file. Since file table overwritten it cannot recover full file name, but just file extension based on type found. It takes hours, or longer if drive is very large. And also requires a large amount of available space on your backup drive to copy all the recovered data to. I have used photorec just to recover some text files. My backup was about a month old. Testdisk found every copy I had saved as it also found all the deleted copies. It took weeks to sort files by viewing them, and then comparing the almost identical files to see which had newer or deleted info in them. Or oldfred backs up better.

If system was a new Windows 8 system, it has always on hibernation. Linux does not mount NTFS needing chkdsk, nor hibernation, so it then does not know about a Windows install. It should see partition exists and not just look for boot files and that has been fixed in the newest version only.

But you must have Windows 8 fast start up or always on hibernation off. And better to use the Something Else install option so you can see exact partitions on drive and choose which you want to use. Or if you choose to install with LVM or LVM with full drive encryption those options are always full drive installs.

 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

You will not recover a bootable Windows. If you did not make the Vendor recover or the Windows recovery which Windows highly recommends, you may be able to get a Vendor restore image from the vendor for shipping charges. Otherwise you have to purchase a new copy of Windows.

---

