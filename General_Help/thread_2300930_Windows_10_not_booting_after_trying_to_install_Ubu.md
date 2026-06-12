---
title: "Windows 10 not booting after trying to install Ubuntu"
date: 2015-10-29
forum: General Help
---

### Post by filon2 on 2015-10-29
Hello everyone, 
yesterday I tried to install Ubuntu 15.10. I already have Windows 10 installed on my PC which is Samsung NP350V5C. When it came to Ubuntu installation I choose the option to manage partitions manually because I didn't want to format disk. (My disk is 500 GB and I didn't make any partitions before.) I realized that I don't know how to use the partition manager and I just clicked some buttons but eventually returned and didn't proceed with installation. I must have clicked some buttons I wasn't supposed to because Windows doesn't boot anymore. I must have done some kind of mess in a file system. When I turn on my computer Windows doesn't boot and only BIOS is booted. However I can boot Ubuntu from USB drive. 

I tried to fix thing using 'Boot-Repair' tool through Ubuntu but it still doesn't work. Now I'm into TestDisk software but I'm stuck in place and I don't know what to do. 

[ATTACH=CONFIG]265235[/ATTACH]

This is a log from TestDisk. It shows that there are a few partitions which I must have created accidentally, but I don't know what to do with them and how to use TestDisk software so basically I'm looking for a step by step solution to make Windows work again. 

Thank You!

---

### Post by leunam12 on 2015-10-29
Can you boot to windows recovery partition? There is an option there to repair boot problems.

---

### Post by filon2 on 2015-10-29
In boot menu (BIOS I mean) I have three options: hard disk, USB and DVD drive; when I try to boot from HD - nothing happens. It tells me to reboot because no OS have been found.

---

### Post by oldfred on 2015-10-29
You show /mapper which is the LVM or LVM with encryption install option. That erases entire hard drive, so all of Windows was erased, and your on disk recovery partition. If Windows 10 or upgrade from Windows 8 you may have installed in either UEFI or BIOS boot mode but still erased everything.

If you did not do a full backup of Windows, you will just have to reinstall. Some vendors will ship you for nominal charge a image of your Windows. It is not a full installer, but just the hard drive image as purchased.
If you have data you did not backup, STOP writing anything to drive. If testdisk deeper search in gpt mode (if UEFI Windows) do not show files, you may be able to recover some data with photorec or Windows recovery tools. Ubuntu install overwrote some data so not all recoverable. But Ubuntu smaller than Windows and writes to entire partition where Windows writes most to beginning of partition.

       [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[URL="http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html"]http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html
[/URL]
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.[URL="http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html"]
[/URL]

---

### Post by filon2 on 2015-11-01
I recovered partition which is shown in the thumbnail on the top position (in the first post of thread) using PhotoRec. Now these recovered files are a total mess and it will take months to go through it. But the question is - should I recover any other position shown on thumbnail? Such as both of the /mapper? Or dm-0, dm-1?

P.S> I mean - will it give other results than recovering the /sda (which I've already recovered) because basically that;s the same partition. Am I wrong?

---

### Post by yancek on 2015-11-01
> should I recover any other position shown on thumbnail? Such as both of the /mapper? Or dm-0, dm-1?

No.  It's the same thing as you can see by the size indicated.  The /dev/mapper you have highlighted in your image shows below as dm-o, same size and the other two are for swap which you can ignore.  As pointed out above, an LVM install overwrites everything so if you install again, do not select that option.

---

### Post by oldfred on 2015-11-01
I have used photorec and yes it took a long time to restore files. In my case I had a good backup, it just was a month old. And I had saved text files many times in that month and wanted those changes. Photorec found each & every file I had saved or all the deleted copies. So I had to find the .txt files that matched backup, and then do many compares.  I now include file name in every text file.

 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by Swagman on 2015-11-01
Windows 10 requires secure boot

Go into BIOS and ensure it's switched ON

---

