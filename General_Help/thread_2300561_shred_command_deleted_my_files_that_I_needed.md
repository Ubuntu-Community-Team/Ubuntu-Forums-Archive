---
title: "shred command deleted my files that I needed"
date: 2015-10-26
forum: General Help
---

### Post by ramin5 on 2015-10-26
Hi guys and sorry for my bad English.
In fact I ran shred command on a 2 TB hdd when was connected a 3 TB hdd too. but seemingly on the way of shred 3 TB was disconnected and again reconnected. dev/sdb changed to something else and it continue shred on my 2 TB hdd and my 3 TB hdd!!!
I didn't want it shred on my 3 TB and I wasn't at home so I get it late.
I really need my data and I stop it on the way when I discovered so it didn't complete its job.
I get image.dd with testdisk and I really need your help.
Is there anyway to recover at least partial of my data with free software?
I googled many sites and instructions but this is my first topic here and I'll be glad if you help me.
Thanks.

---

### Post by oldfred on 2015-10-26
When you plug & unplug external devices, drives, flash drives or multicard readers, you may get many different drive like sdb for the same drive. You really have to pay attention.
And shred is totally destructive. Whatever it ran on is totally gone.

If you have stopped it in time to save some data, testdisk and probably photorec are free choices. It partition was NTFS, some Windows tools may work better.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

I have used photorec. It takes forever, it was overnight on my much smaller drive. It actually is just scanning drive for anything that looks like a file. And it recovers everything, but not by filename, just extension. I have saved some .txt files many times and it found all the deleted ones. I had to do many compares and check with my last backup to add found data. But was never sure I found the last saved version.


 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

      
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
Caution: getdataback is not the same and is a scam.

---

### Post by ramin5 on 2015-10-27
thank you for your time and suggestion. I've used them and I've read them. I attach a pic from image in hexedit. These things are not zero, is it mean there is any hope to recovery or not? I couldn't get good resualts from testdisk and even photorec. Should I recover partition table that have been damaged? for example with gpart? gpart is not an old software? testdisk couldn't found a complete partition table. it found some partition table but they were split and incomplete and I couldn't see my files from that partition tables. Or should I use geometry in testdisk? also if you can give me link of some topics that they have my problem I'll be appreciate. maybe they could recover and I can find something good from theirs topics.
by the way, if I manipulate geometry of image.dd, testdisk will save my changes on image or my changes are temporary and whenever I exit from testdisk, testdisk will not save my changes?
Thanks.

---

### Post by oldfred on 2015-10-27
Was partitioning MBR(msdos) or gpt? And then did you load testdisk in same mode?

Do you know exact (sector) of drive? If you even have a good idea parted rescue can also work if partitions are still there.

These were more where Windows deleted the Linux partition in the partition table and that just had to be restored.
       Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)#

---

### Post by ramin5 on 2015-10-27
It's MBR(msdos). a NTFS Partition. yeah, I used once testdisk in analyse mode, once in Advanced and its process.
Because it's a 3 TB all of the process take a very long time. so I'm using a 2 gig fat 32 flash memory that I have run shred on it to see any of these software could find partition table or not. (if you have such a small flash memory can you run shred on it? because all of your suggestion are good for deleted partition tables but for shred they are not good.)
of course I've do these process on 3 TB, actully before I want create thread here.
and I couldn't find any thread that have same problem.
I used gpart in terminal. I typed "sudo parted /dev/sdc unit s print" and prompt me "Error: /dev/sdc: unrecognised disk label". and I used it in gparted. in Attempt Data Rescue from Device menu.
after that I continued your instruction and entered start and end but in a moment show me progress bar but after that disappeared.
I mounted image.dd but it was completely free.
I used testdisk, photorec and some other software but none of them could find even one file and still I couldn't even one file recovery!
completely hopeless!
do you think should I give it up?
thanks.

---

### Post by oldfred on 2015-10-28
If photorec or some of Windows tools do not find data then it may have been totally erased.

I understand shred writes random data, so that my be all you are seeing. I have never used shred.
 Secure delete shred :
[http://www.linux.com/learn/tutorials/406976:weekend-project-scrub-files-and-old-hard-drives-securely-on-linux](http://www.linux.com/learn/tutorials/406976:weekend-project-scrub-files-and-old-hard-drives-securely-on-linux)

---

