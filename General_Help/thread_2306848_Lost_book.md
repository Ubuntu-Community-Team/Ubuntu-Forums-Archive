---
title: "Lost book"
date: 2015-12-19
forum: General Help
---

### Post by CordeTheAwesome on 2015-12-19
Ok so here's the problem: 

A while ago I had Ubuntu 15.04. I've had Linux before, Ubuntu specifically, but always did away with it eventually.  But I got it again and though the os was relatively new,  it started having problems. I can't go into detail about this because I'm not exactly sure what was going on. I remember I just want able to log in and use the os regularly. I kept getting stuck on this one screen.  The root of the problem too is unknown. However, it could be due to a partition problem that I had been trying to fix with GParted that never worked.  Ultimately, I ended up deleting the partition completely. 

This wouldn't be a problem considering that my computer was dual booted with Windows 8 and I rarely saved anything to Ubuntu anyways.  Unfortunately,  the one thing I did save was a book I was writing. 

Obviously,  this loss was very regrettable.  The book was a good ways along and pretty awesome too. But I figured  if I didn't address the problem, then it would go away.  This idea worked somewhat. Then I realized when I thought about the fact that I lost my book I only thought about just that the fact and not the consequence. The other night I really reflected on this tragedy and almost bright my self to tears.

Anyways,  I have Windows 10 (after an upgrade) dual booted with Ubuntu 15.10 now (after reinstalling Ubuntu once again) on the same computer. Of course,  the book is not there. But is there anyway I can get it back? 
 
If no,  I will cry virtual tears and if yes, whoever contributed the resolution deserves a virtual hug.

Please help.

---

### Post by dragonfly41 on 2015-12-19
The golden rule when you have any data loss (such as deleted file) is to immediately stop what you are doing .. otherwise in time the data might be overwritten by some other process.

You then need to shut down and boot up a Live CD or Live USB (Ubuntu) to run forensic tests to try to recover the lost data in your partition.

Now you have written that you "deleted" the problem ubuntu partition and reinstalled Ubuntu 15.04.   There is a slim chance that your deleted data is still buried away in your Ubuntu partition .. but don't use it any further.

If you have a Live USB or Live CD use that to inspect your latest Ubuntu OS partition in testdisk.   I suggest that you stay in Windows 10 or Live USB Ubuntu to study more about what testdisk might achieve.   Search about "forensic data recovery" in this forum. But stop using your existing Ubuntu OS (internal partition) until you check if you can retrieve the lost book.  And next time use backup procedures.

There are many examples of using testdisk.  Go to the testdisk developer's site to learn more.

---

### Post by oldfred on 2015-12-19
The more valuable the data, the more ways and frequency of backup required.
Hard drives fail, Lighting strikes, and all the usual kid, cat, dog pressed wrong keys issues.

And recovery really only possible before new install or upgrade.
But if you did not zero our drive, you may have data somewhere. Did you have a separate /home or data partition for your own data? Or saved to a NTFS shared data partition?

There is a part of testdisk called photorec. Not just for recovery of photos. It scans drive for anything that looks like a file. It will not recovery full file name, just extension by type. If you know extension you used you can narrow search, but it still takes just as long. My search for text files on a relatively smaller drive took overnight. And it found many text files including versions I had deleted. But I had not reinstalled, and files were smaller, so chance of being overwritten were smaller.

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[URL="http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"]http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step
[/URL]
 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

[URL="http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step"]
[/URL]

---

### Post by coldraven on 2015-12-20
Sorry to hear about your lost book. Follow the advice given above and you may have a chance of recovering it.
I wanted to tell you about backups. **The frequency of backups is in direct proportion to the value of the data.** 
For example, a big company might have 50 people typing in invoices. If they lose a days worth of data that would be 50 x 8 = 400 people hours to re-type all those invoices. In the meantime more invoices are building up so they would be hard pressed to catch up with all this work. That's why they do a backup each hour! So when (not if!) it all goes wrong they have only lost 50 people hours, just doing one hour overtime will get them back on track.
You have to learn to estimate how many hours work you may lose in relation to how long would it would have taken to create a backup. (or multiple backups for really important stuff)
Hope it works out.

---

### Post by CordeTheAwesome on 2015-12-21
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
And recovery really only possible before new install or upgrade.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Does this mean I can't recover anything?

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
But if you did not zero our drive, you may have data somewhere. Did you  have a separate /home or data partition for your own data? Or saved to a  NTFS shared data partition?
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I'm not really sure what this means at all ^^.

> **dragonfly41 said:**
> The golden rule when you have any data loss (such as deleted file) is to immediately stop what you are doing .. otherwise in time the data might be overwritten by some other process.

You then need to shut down and boot up a Live CD or Live USB (Ubuntu) to run forensic tests to try to recover the lost data in your partition.

Now you have written that you "deleted" the problem ubuntu partition and reinstalled Ubuntu 15.04.   There is a slim chance that your deleted data is still buried away in your Ubuntu partition .. but don't use it any further.

If you have a Live USB or Live CD use that to inspect your latest Ubuntu OS partition in testdisk.   I suggest that you stay in Windows 10 or Live USB Ubuntu to study more about what testdisk might achieve.   Search about "forensic data recovery" in this forum. But stop using your existing Ubuntu OS (internal partition) until you check if you can retrieve the lost book.  And next time use backup procedures.

There are many examples of using testdisk.  Go to the testdisk developer's site to learn more.


I can't really stop what I'm doing. I do not have anything to make a Live USB or Live CD. Do I need to do this?

> **coldraven said:**
> Sorry to hear about your lost book. Follow the advice given above and you may have a chance of recovering it.
I wanted to tell you about backups. **The frequency of backups is in direct proportion to the value of the data.** 
For example, a big company might have 50 people typing in invoices. If they lose a days worth of data that would be 50 x 8 = 400 people hours to re-type all those invoices. In the meantime more invoices are building up so they would be hard pressed to catch up with all this work. That's why they do a backup each hour! So when (not if!) it all goes wrong they have only lost 50 people hours, just doing one hour overtime will get them back on track.
You have to learn to estimate how many hours work you may lose in relation to how long would it would have taken to create a backup. (or multiple backups for really important stuff)
Hope it works out.

Yeah I hear about backing up a lot. But I'm literally living on the edge. I don't have anything with enough space to back up my most important stuff.

---

### Post by sudodus on 2015-12-21
In order to avoid further damage, please do not boot your computer from the system on your hard disk drive.

Instead maybe you can borrow a computer or ask a friend, colleague or relative to help you get or make a CD/DVD boot disk or USB boot drive with Ubuntu or some linux rescue system.

Then you can boot your computer from the CD/DVD/USB boot drive and run some recovery programs. You will also need a drive where you can store the data, that you manage to recover, the manuscript of your book and maybe some other important files. It could be a USB pendrive (big enough for the file(s) that you intend to save).

Do you remember how it was saved, what kind of file? Was it an open office text document, an odt file, or a Microsoft Word document .doc, or some other file type? If you use ***PhotoRec*** to recover the manuscript, it helps a lot if you know what kind of file it was.

See this link

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

[File_Formats_Recovered_By_PhotoRec#Office](http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec#Office)

---

### Post by Bucky Ball on 2015-12-21
I suggest you create a [SystemRescueCD]("http://sourceforge.net/projects/systemrescuecd/") bootable media (it can be disk or USB) and boot from that. It includes everything you're going to need, Testdisk and Photorec to name a couple, but to be honest, don't like your chances as you have done a lot with this disk since the problem.

And yes, as suggested, do this on another machine. Avoid using that disk for anything but retrieving data from it. 

Good luck, though. :)

PS: Before starting on version two of the book, suggest you get a USB stick to back it up to. If you really can't manage that much, at least you'll be alert to the fact that this could happen again at any time and won't be in shock if it does happen again. You may have a book that is never finished ... for all the wrong reasons.

PPS: If you can't manage any kind of physical backup, email it to a friend or send it to 'the cloud'. Other than that, develop a photographic memory? :-k

---

### Post by dragonfly41 on 2015-12-21
> I can't really stop what I'm doing. I do not have anything to make a Live USB or Live CD. Do I need to do this?

But I'm literally living on the edge. I don't have anything with enough space to back up my most important stuff.


So let's try recovery with what you do have right now. i.e. not using Live CD or Live USB.

You write that you have a working Windows 10 on the same hard drive.
Make sure that you are now working in Windows 10.

Now read here ...

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Still in Windows 10 download and install testdisk executable (for Windows).

Launch testdisk from Windows command line.

You can proceed to the first stage to allow testdisk to analyse your hard drive and post back results here.  
This should list all your partitions .. Windows 10 and Ubuntu.

Later you can proceed to analyse the Ubuntu partition in testdisk Advanced mode.

This is your guide ... [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2)


Likewise you can run photorec in Windows 10.

[later edit]

I would just add a caveat. If you "can't stop what you are doing" then the above approach may not work since your computer may have to be left a long time chuntering away looking for your lost book.  Be prepared to leave testdisk running overnight (or longer).   But the initial testdisk analysis stage is worth running to give more information on your partitions.

---

### Post by CordeTheAwesome on 2015-12-21
> **sudodus said:**
> In order to avoid further damage, please do not boot your computer from the system on your hard disk drive.

Instead maybe you can borrow a computer or ask a friend, colleague or relative to help you get or make a CD/DVD boot disk or USB boot drive with Ubuntu or some linux rescue system.

Then you can boot your computer from the CD/DVD/USB boot drive and run some recovery programs. You will also need a drive where you can store the data, that you manage to recover, the manuscript of your book and maybe some other important files. It could be a USB pendrive (big enough for the file(s) that you intend to save).

Do you remember how it was saved, what kind of file? Was it an open office text document, an odt file, or a Microsoft Word document .doc, or some other file type? If you use ***PhotoRec*** to recover the manuscript, it helps a lot if you know what kind of file it was.

See this link

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

[File_Formats_Recovered_By_PhotoRec#Office]("http://www.cgsecurity.org/wiki/File_Formats_Recovered_By_PhotoRec#Office")




Yes it was definitely .odt which I'm aware is saved as .zip in testdisk.

Another thing is since I've deleted this partition shouldn't I use testdisk instead because it finds lost partitions?

I do not have a usb or cd and I do not have any friends in the area who would help me out. My only option is to order online which could take several days. Is this really necessary? I've been using my computer for at least five months after I deleted that partition.

---

### Post by sudodus on 2015-12-22
I wrote "In order to avoid further damage, please do not boot your computer from the system on your hard disk drive". But after using the drive for five months the damage is probably already done. It is your decision what to do. We only give advice.

Testdisk might or might not be able to repair the file system. PhotoRec can work without a file system. But the data must still be there (not overwritten). Try with both tools according to the description at

[http://www.cgsecurity.org](http://www.cgsecurity.org)

***Edit:*** The way I know is to boot the computer from another drive (not the one from which you want to recover data). But you can try even if it is not recommended. It might work.

---

### Post by jeffjohn2 on 2015-12-22
Hoping you succeed!  When the dust has settled, look into Dropbox; a brilliant, safe way to store additional backups, accessible from anywhere and can be shared!  Best of luck!

---

### Post by CordeTheAwesome on 2015-12-22
Actually I've been running test disk and I can tell its already found my lost partition. The issue now is that in the Step-by-Step guide it indicates to click "Write" but I do not have enough space to write this partition to my hard drive again. When I reinstalled Ubuntu I gave the partition less space. I just want that one file specifically. Now how do I get it?

---

### Post by dragonfly41 on 2015-12-22
Have you been running testdisk in Windows 10 to analyse your lost Ubuntu partition?

You should now be able to save (write) individual files instead of entire partition.

Reminder .. refer to third image in this page .. [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2)

Look at the recovery of an individual file.

---

### Post by CordeTheAwesome on 2015-12-22
> **dragonfly41 said:**
> Have you been running testdisk in Windows 10 to analyse your lost Ubuntu partition?

You should now be able to save (write) individual files instead of entire partition.

Yes I've been using Windows 10.
And I didn't know you could do that. I guess I wasn't sure what "Write" meant.

---

### Post by dragonfly41 on 2015-12-22
Just a point to remember .. above testdisk guide refers to ext2 but at bottom of page there is a suggestion that 
[COLOR=#252525][FONT=sans-serif]photorec can be used to recover ext3 and ext4 
> Note that it [photorec] can recover deleted files from ext3 and ext4 filesystem.[/FONT][/COLOR]
So you could also try photorec from within Windows 10 if testdisk doesn't recover your book file.

---

### Post by CordeTheAwesome on 2015-12-22
Yes I'm doing both. The search finished but it said "the following partitions weren't able to be recovered" or something like that so I'm trying one more time using both methods.

---

### Post by Bucky Ball on 2015-12-23
If you want one file forget testdisk. It is not for that ... at all. Photorec is your only friend.

---

### Post by Rocky_Bennett on 2015-12-23
Although on the face of it, this sounds like a very big problem but you have to remember how many great books were lost and then re-written. Ray Bradbury in particular was famous for losing completed books, and he had to re-write entire books from scratch before the publisher's deadline. Aldous Huxley and Ernest Hemmingway have both lost books that had to be completely re-written from scratch before the publisher's deadline. On a side note, Jimi Hendrix and Jethro Tull have lost complete albums that had to be re-recorded and re-mixed before their respective deadlines. So you are not alone in this delema.

---

### Post by HermanAB on 2015-12-23
It may be better to start writing the sequel.

---

### Post by CordeTheAwesome on 2015-12-23
> **Bucky Ball said:**
> If you want one file forget testdisk. It is not for that ... at all. Photorec is your only friend.

OK thanks. Noted.

> **Rocky_Bennett said:**
> Although on the face of it, this sounds like a very big problem but you have to remember how many great books were lost and then re-written. Ray Bradbury in particular was famous for losing completed books, and he had to re-write entire books from scratch before the publisher's deadline. Aldous Huxley and Ernest Hemmingway have both lost books that had to be completely re-written from scratch before the publisher's deadline. On a side note, Jimi Hendrix and Jethro Tull have lost complete albums that had to be re-recorded and re-mixed before their respective deadlines. So you are not alone in this delema.

Wow. Interestingly enough I was going to counter your argument by saying my book wan't just any childish book because it has a philosophical aspect to it. And then you mentioned Bradbury and Huxley and I was like, "Well dang it. I guess I don't have any excuses now."

You guys are right. If all fails, I'll start on that task this summer. It's just hard because I can remember so much but I will constantly be reminded that it's not the same and never will be and at the same time I will always have this idea that the first version was better. The worst part is that all my book notes were saved on that same document as well! :icon_frown:

Anyways, thanks everyone for all the help. After this last scan photorec which will likely take overnight at least, I let you guys know the outcome-- presumably an unfortunate one.

---

### Post by dragonfly41 on 2015-12-23
Nice to see that you are making progress .. here is one explanation of "the harddisk seems too small" .. 
hope you have not closed down your session .. you will need to keep your computer running to avoid starting another search

[http://askubuntu.com/questions/400150/how-to-resolve-the-harddisk-seems-too-small-with-testdisk-deeper-search-optio](http://askubuntu.com/questions/400150/how-to-resolve-the-harddisk-seems-too-small-with-testdisk-deeper-search-optio)

You will see the same message you report .. "harddisk too small" .. in this walkthrough ..

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[I]
[FONT=-apple-system]"In our case, our small hard drive has previously been formatted as NTFS. Amazingly, TestDisk finds this partition, though it is unable to recover it."[/FONT][/I]

Have you run deeper search?

Next time you use testdisk (if you have to shut down) I suggest that you add option to create log file for future reference.

There is also the cgsecurity.org forum for more advice.

[http://forum.cgsecurity.org/phpBB3/help-drive-too-small-partition-ends-after-disk-limits-t325.html](http://forum.cgsecurity.org/phpBB3/help-drive-too-small-partition-ends-after-disk-limits-t325.html)

...

Be aware that since you have Windows 10 working in separate partition there are other Windows native recovery tools you could try on your lost Ubuntu partition.

Here is one .. [http://www.diskinternals.com/linux-recovery/](http://www.diskinternals.com/linux-recovery/)

and another .. [http://www.easeus.com/datarecoverywizard/recover-ext2-ext3-drive.htm](http://www.easeus.com/datarecoverywizard/recover-ext2-ext3-drive.htm)

Finally .. [http://www.piriform.com/recuva/download](http://www.piriform.com/recuva/download)

---

### Post by CordeTheAwesome on 2015-12-23
> **dragonfly41 said:**
> Nice to see that you are making progress .. here is one explanation of "the harddisk seems too small" .. 
hope you have not closed down your session .. you will need to keep your computer running to avoid starting another search

[http://askubuntu.com/questions/400150/how-to-resolve-the-harddisk-seems-too-small-with-testdisk-deeper-search-optio](http://askubuntu.com/questions/400150/how-to-resolve-the-harddisk-seems-too-small-with-testdisk-deeper-search-optio)

You will see the same message you report .. "harddisk too small" .. in this walkthrough ..

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[I]
[FONT=-apple-system]"In our case, our small hard drive has previously been formatted as NTFS. Amazingly, TestDisk finds this partition, though it is unable to recover it."[/FONT][/I]

Have you run deeper search?

Next time you use testdisk (if you have to shut down) I suggest that you add option to create log file for future reference.

There is also the cgsecurity.org forum for more advice.

[http://forum.cgsecurity.org/phpBB3/help-drive-too-small-partition-ends-after-disk-limits-t325.html](http://forum.cgsecurity.org/phpBB3/help-drive-too-small-partition-ends-after-disk-limits-t325.html)

...

Be aware that since you have Windows 10 working in separate partition there are other Windows native recovery tools you could try on your lost Ubuntu partition.

Here is one .. [http://www.diskinternals.com/linux-recovery/](http://www.diskinternals.com/linux-recovery/)

and another .. [http://www.easeus.com/datarecoverywizard/recover-ext2-ext3-drive.htm](http://www.easeus.com/datarecoverywizard/recover-ext2-ext3-drive.htm)

Finally .. [http://www.piriform.com/recuva/download](http://www.piriform.com/recuva/download)


Yes I've tried both of those last two for Windows. Both did not recognize my entire device, only the Windows partition. Linux Recovery seems hopeful though.

 I did use "Create log file". I'm not sure what it does however or where this so called "log file" is. Thanks for the articles though. I'm looking into to them now.

And this partition was found with "Deeper search" actually.

Another question I have is that does "Write" mean it will write the partition to my device? Because if that's so then that may be the problem because I already have Ubuntu. I'm open to deleting it though for space.

---

### Post by dragonfly41 on 2015-12-24
"Write" refers to write partition _table_ .. not the partition filesystem

As a precaution perhaps you could backup/note your existing partition table in case you need to recover it.

  sudo sfdisk -d /dev/sda

You don't want your working Windows 10 to become unbootable. 
On that thought do you have a Windows recovery CD?
Should have mentioned that before starting your recovery session.

Referring back to your earlier post ..
[COLOR=#000000]> I do not have anything to make a Live USB or Live CD. Do I need to do this?
It is really essential to have some method to fall back on in the event that you find you can't bootup.
A USB flash to contain a Live USB is not costly.
[/COLOR]
testdisk log file should be in Windows root directory.

---

### Post by CordeTheAwesome on 2015-12-24
> **dragonfly41 said:**
> "Write" refers to write partition _table_ .. not the partition filesystem

As a precaution perhaps you could backup/note your existing partition table in case you need to recover it.

  sudo sfdisk -d /dev/sda

You don't want your working Windows 10 to become unbootable. 
On that thought do you have a Windows recovery CD?
Should have mentioned that before starting your recovery session.

Referring back to your earlier post ..
[COLOR=#000000]
It is really essential to have some method to fall back on in the event that you find you can't bootup.
A USB flash to contain a Live USB is not costly.
[/COLOR]
testdisk log file should be in Windows root directory.

Well I'm still running photorec so I can't do anything with Ubuntu right now.

No, I don't have a Windows recovery CD? What is that exactly?

If I get a CD or flashdrive, how much space does it need? And the thing is I don't have one readily available and so I will have to wait for it to ship. I'm afraid that by that time, especially since it's Christmas, this forum will be all but non-existent. If I leave a forum alone for even one day people often stop replying.

Also should I get rid of Ubuntu or not for the partition that "cannot be recovred"? This really won't be a problem since I have nothing on there but I just need to know if it's necessary.

---

### Post by oldfred on 2015-12-24
Windows repair CD or flash is small. Years ago I made a Windows 7 repair flash drive on a 2GB flash drive and it used about 300 or 400MB. So you can easily use a CD, but I find I do not use CDs except to give larger numbers of photos to friends. I do use DVDs to make backups of my most critical data, but now have to use 2 just for photos, something about grandkids and lots more pictures.

I have a Microcenter store nearby and they have always had flash drives for a good price behind cash register. I have to limit my visits as I get a new flash drive every time I go. They are always lower in cost or next size up is price I paid before. And now I only get USB3 as they are a bit faster even on USB2 ports.

You can always bump a thread after 24 hours to move it back into first pages where someone usually sees it. 
I search forum for any threads, I have posted in, and any new post even after years is at top of search.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

I think process is almost same across all recent versions of Windows.

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)

---

### Post by dragonfly41 on 2015-12-24
Another tip .. While you remain in Windows 10 (for now) you can use unetbootin (Win download) to create from Windows a Ubuntu Live USB (when you do get a flash drive). 
My old flash drive is only 8GB in size. You can buy these in most stores/supermarkets without need to order by post.

[http://unetbootin.github.io/](http://unetbootin.github.io/)

There is also a Ubuntu version of unetbootin but you are not working in Ubuntu right now.

---

### Post by CordeTheAwesome on 2015-12-24
So you want me to back up Windows 10 and use an Ubuntu Live USB to run testdisk again? Right?

And once again I ask: should I get rid of Ubuntu or not for the partition that "cannot be recovred"? This really won't be a problem since I have nothing on there but I just need to know if it's necessary.

If this fixes the problem it fixes all the problems.

---

### Post by dragonfly41 on 2015-12-24
No. The advice offered is in effect you are attempting recovery without the right tools.

The lack of a Windows recovery CD (or USB) or Ubuntu Live USB does makes me cautious in offering more advice.
You would not be backing up Window 10 but instead having a means of recovering from errors (such as inadvertently overwriting MBR or partition table).
In such an event you would have no means of getting back into your computer.

I would at least write down on paper the partition table details you have from your testdisk log file (if you have now found it in c:/ root directory in Windows).

To clarify, since you are running from Windows it is not essential that you create a Live Ubuntu USB.

But if you can put your recovery project on hold and enjoy Christmas for the next few days and return to this thread when you have these tools at hand it would make the recovery task that much easier for all contributors.

[later edit]

And next time you bootup your PC .. check that the PC bios can boot from USB (see the BIOS menu at boot up .. press F12 at bootup for one time boot settings).

I have in my own setup (laptop) a dual boot configuration containing Windows, and two separate installations of Ubuntu.  I can then use one Ubuntu installation instead of a Live USB (although I also have a Live USB to fall back on).

To answer your question on next step after partition cannot be recovered I would first note down my partition table and then hit enter and hope for the best. 
The worst case scenario is that you would then have to attach your non bootable drive to another working PC to recover it.

---

### Post by CordeTheAwesome on 2015-12-24
> **dragonfly41 said:**
> No. The advice offered is in effect you are attempting recovery without the right tools.

The lack of a Windows recovery CD (or USB) or Ubuntu Live USB does makes me cautious in offering more advice.
You would not be backing up Window 10 but instead having a means of recovering from errors (such as inadvertently overwriting MBR or partition table).
In such an event you would have no means of getting back into your computer.

I would at least write down on paper the partition table details you have from your testdisk log file (if you have now found it in c:/ root directory in Windows).

To clarify, since you are running from Windows it is not essential that you create a Live Ubuntu USB.

But if you can put your recovery project on hold and enjoy Christmas for the next few days and return to this thread when you have these tools at hand it would make the recovery task that much easier for all contributors.

[later edit]

And next time you bootup your PC .. check that the PC bios can boot from USB (see the BIOS menu at boot up .. press F12 at bootup for one time boot settings).

I have in my own setup (laptop) a dual boot configuration containing Windows, and two separate installations of Ubuntu.  I can then use one Ubuntu installation instead of a Live USB (although I also have a Live USB to fall back on).

To answer your question on next step after partition cannot be recovered I would first note down my partition table and then hit enter and hope for the best. 
The worst case scenario is that you would then have to attach your non bootable drive to another working PC to recover it.

I know it can. I actually have an Ubuntu Live USB but it's not with me as I'm spending Christmas away from home.

Luckily, however, I was finally able to get a flashdrive (8 GB)!

What exactly should I do now?

---

### Post by Bucky Ball on 2015-12-24
Christmas doesn't make a lot of diff around here. We are an international forum and Christmas isn't as significant in many parts of the world (we are not all in America or the UK :)).

Don't fear. This is a long and active thread with a lot of heads contributing, so it's not going to disappear overnight. :D

---

### Post by dragonfly41 on 2015-12-25
Resuming discussion ..

While you are still in Windows, and before creating a Live Ubuntu USB on your 8Gb flash, you might try installing Stellar Phoenix Linux Data Recovery in Windows.

[http://www.stellarinfo.com/linux-data-recovery.php](http://www.stellarinfo.com/linux-data-recovery.php)

and try recovery on Linux partitions.
If that doesn't work ... follow these next steps ...

...

I booted into my dual boot Windows Vista partition to check the workflow below.

Downloaded .. [https://unetbootin.github.io](https://unetbootin.github.io)

I tried to install in my Windows but surprised to see error message ..

"unetbootin-windows-613.exe is not a valid win32 application"

Searched around ...

[http://ubuntugeeknerd.blogspot.co.uk/2012/11/unetbootin-install-not-valid-win32.html](http://ubuntugeeknerd.blogspot.co.uk/2012/11/unetbootin-install-not-valid-win32.html)

So I must amend my earlier advice to you to use unetbootin in Windows.

Install alternative tool in Windows ..

Universal-USB-Installer-1.9.6.2.exe from

[http://pendrivelinux.win/universal-usb-installer-easy-as-1-2-3/](http://pendrivelinux.win/universal-usb-installer-easy-as-1-2-3/)

But also check that you have enough head space (up to 1GB) in Windows 10 partition to receive downloaded Ubuntu iso file.

Download 14.04 desktop from here ... [http://www.ubuntu.com/downloads/desktop](http://www.ubuntu.com/downloads/desktop)

Do you have any files on the 8GB flash drive that need to be backed up?

Go through installation steps 1,2,3,4 in Universal-USB-Installer double checking that you have selected the ISO file and the target USB drive.

Read here (although an old tutorial referring to Ubuntu 9 it is still helpful) ...

[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

and ensure that at Step3 you tick format USB Flash Drive as FAT32

and at Step 4 you select persistence option which allows you to save files into your Live USB. Perhaps saving files recovered from testdisk run.

Here is a more up to date tutorial ...

[http://popey.com/blog/2015/03/25/making-a-portable-persistent-ubuntu-usb-stick/](http://popey.com/blog/2015/03/25/making-a-portable-persistent-ubuntu-usb-stick/)

And other guides on creating persistent storage ...

[http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb](http://askubuntu.com/questions/397481/how-to-make-a-persistent-live-ubuntu-usb-with-more-than-4gb)

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)


Now you can test your Live USB by setting USB as first boot option in your computer BIOS menu
to run from Live USB choosing "Try Ubuntu".


When you have the Ubuntu Live USB up and running you will need to install some recovery tools.

First install boot-repair using 2nd option documented here here ..

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

When installed run boot-repair and take a note of the pastebin link you receive after clicking on "Recommended Repair".

Next install latest testdisk into the Live USB (but not from repo since you should download the latest version of testdisk).

The older version in my Ubuntu 14.04 repo is 6.14.2.

Latest stable version is 7.0 April 18th 2015

Download from here ...

[http://www.cgsecurity.org/Download_and_donate.php/testdisk-7.0.linux26.tar.bz2](http://www.cgsecurity.org/Download_and_donate.php/testdisk-7.0.linux26.tar.bz2)

and read here ...

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)


Unzip and copy testdisk-7.0 folder to (typically) home/<user>/ directory.

i.e. ~/testdisk-7.0

Open terminal in that folder ..

cd ~/testdisk-7.0

[COLOR=#252525]Under Unix/Linux/BSD, you need to be root to run TestDisk 

ie. [/COLOR]sudo ~/testdisk-7.0/testdisk_static

If you see an older version of testdisk by running testdisk you may need to purge older version of testdisk.

Now in testdisk window ..

Analyse > Analyse current partition structure

After Analyse step use arrow right to switch from [Quick Search] to [Backup]

Save current partition list to backup.log file and proceed

Hit Enter


At this point look in ~/testdisk-7.0 folder for
backup.log
testdisk.log

You could post contents of these files at [http://pastebin.com/](http://pastebin.com/) and post the link here for reference.

You can also try photorec by running [COLOR=#252525]ie. [/COLOR]sudo ~/testdisk-7.0/photorec_static

Unfortunately you don't have a backup drive otherwise the advice would be to create an image of your Ubuntu partition and then try to recover data from that image.

Now with Live USB (persistent mode) working you can begin to analyse your Ubuntu partition where hopefully the lost book *_might_* be lurking.

Continue not to use the Ubuntu OS which might contain lost book.

And .. since you are in the last chance saloon and you are specifically searching for an ***.odt file** - the lost book - I'm throwing into the pool this forensic approach using scalpel. 

If you install scalpel in your Live USB you will find a configuration file in 
sudo gedit /etc/scalpel/scalpel.conf

The default scalpel.conf does not include *.odt filters and so add the filters listed here ...

[http://ubuntuforums.org/showthread.php?t=1378119](http://ubuntuforums.org/showthread.php?t=1378119)

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

You can then run scalpel in Live USB with all other extensions commented out in scalpel.conf .. i.e. only *.odt extension enabled.

Other examples here ... [http://community.linuxmint.com/tutorial/view/1332](http://community.linuxmint.com/tutorial/view/1332) and here [http://stackoverflow.com/questions/22542527/recovering-odt-file-using-scalpel](http://stackoverflow.com/questions/22542527/recovering-odt-file-using-scalpel)

Apply scalpel to the partition which holds your internal Ubuntu.   
And define the location where any recovered files can be saved (e.g. in your persistent Live USB, not the partition you are analysing).

Note that this should be regarded as an experiment.

---

### Post by CordeTheAwesome on 2015-12-26
Thanks guys! I am using all your advice.

Scalpel looks reliable so I'm trying that first.

After that I'll try using testdisk again, this time with the LiveUSB. And then of course photorec.

And if none of those work I'll try my odds with something called foremost I've heard about.

Then... I'll give up.

I'll keep you all posted.

---

### Post by Rocky_Bennett on 2015-12-26
Good luck. I hope everything turns out good.

---

### Post by CordeTheAwesome on 2015-12-26
The general problem now with all these programs seems to be that there isn't enough space to save my problems.

I guess that means I should get a flashdrive with more space?

---

### Post by dragonfly41 on 2015-12-28
Of course you will need some headroom to save any recovered files. 
Post #41 above did advise that you paste some details of your system to pastebin so that we can assess how much space you have in your drive.

If you don't have enough free space in your internal drive you should have quite a bit of space left in your 8 GB Live USB to receive at least some of these files. Scalpel should provide a narrower list of files.

One further thought ...

Looking back at your first post (#1) you write that you had Windows 8 then saved your book (written in Windows 8 ?) to Ubuntu 15.04. After that you upgraded Windows 8 to Windows 10 dual boot with Ubuntu 15.04.

Now if at one stage you had your lostbook in Windows 8 partition have you tried recovery of *.odt files from your Windows partition - albeit an upgraded Windows?

I don't hold much hope of finding this file after the various upgrades and time which has elapsed but it will be a useful learning process for future data recovery.

---

### Post by CordeTheAwesome on 2015-12-28
> **dragonfly41 said:**
> Of course you will need some headroom to save any recovered files. 
Post #41 above did advise that you paste some details of your system to pastebin so that we can assess how much space you have in your drive.

If you don't have enough free space in your internal drive you should have quite a bit of space left in your 8 GB Live USB to receive at least some of these files. Scalpel should provide a narrower list of files.

One further thought ...

Looking back at your first post (#1) you write that you had Windows 8 then saved your book (written in Windows 8 ?) to Ubuntu 15.04. After that you upgraded Windows 8 to Windows 10 dual boot with Ubuntu 15.04.

Now if at one stage you had your lostbook in Windows 8 partition have you tried recovery of *.odt files from your Windows partition - albeit an upgraded Windows?

I don't hold much hope of finding this file after the various upgrades and time which has elapsed but it will be a useful learning process for future data recovery.

It won't allow me to save to the actual computer only the flash drive and doesn't let me narrow the list of files. 

Also,  I've already tried testdisk and photorec in Windows.  It found the partition but it said it could not be recovered.  And photorec was taking several days.

---

### Post by dragonfly41 on 2015-12-28
Just to double check .. when you write "[COLOR=#000000]Also, I've already tried testdisk and photorec in Windows."

Do you mean ..

(a) I ran scalpel/testdisk/photorec from within Windows and analysed my Ubuntu partition
or
(b) I ran scalpel/testdisk/photorec from within Live USB and analysed my Ubuntu partition
or
(c) I ran scalpel/testdisk/photorec from within Live USB and analysed my Windows partition.


[later edit]
I've just taken a look inside my Live USB flash and I have 5.5 Gb free out of 7.5 Gb.
You can save quite a few files in 5.5 Gb. And scalpel if setup properly doesn't need that amount of space.
Scalpel.conf does allow you to filter files as explained earlier.
Here is another explanation ... [/COLOR][http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel](http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel)

---

### Post by CordeTheAwesome on 2015-12-28
> **dragonfly41 said:**
> Just to double check .. when you write "[COLOR=#000000]Also, I've already tried testdisk and photorec in Windows."

Do you mean ..

(a) I ran scalpel/testdisk/photorec from within Windows and analysed my Ubuntu partition
or
(b) I ran scalpel/testdisk/photorec from within Live USB and analysed my Ubuntu partition
or
(c) I ran scalpel/testdisk/photorec from within Live USB and analysed my Windows partition.


[later edit]
I've just taken a look inside my Live USB flash and I have 5.5 Gb free out of 7.5 Gb.
You can save quite a few files in 5.5 Gb. And scalpel if setup properly doesn't need that amount of space.
Scalpel.conf does allow you to filter files as explained earlier.
Here is another explanation ... [/COLOR][http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel](http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel)

(a) and now that you ask that question I realize what you meant. But what I said in my original post was that I wrote a book in Ubuntu 15.04 and saved it there as well. The dual-boot stuff is just background information for you all to know there weren't any major consequences to altogether deleting my Linux partition. 

The article didn't help much with my problem. :(

---

### Post by dragonfly41 on 2015-12-28
I'm now testing my own suggestions and have compiled scalpel-2.0 as per previous article.
The following packages need to be installed in Ubuntu 14.04 or ./configure does not work
  tre-agrep
  libtre5
  libtre-dev
The scalpel version in Ubuntu repo is older.   1.60-1build1
I'm applying scalpel-2.0 to a backup /home folder as I write this.
I'll advise progress later .. in about 5 minutes it has processed 50% of first pass (of two passes).

I was able to complete a testrun on /home using scalpel-2.0 
aiming for pdf files.

```

scalpel -c /etc/scalpel/scalpel.conf -o ~/scalpel_test /dev/sda11
Scalpel version 2.0
Written by Golden G. Richard III and Lodovico Marziale.
Multi-core CPU threading model enabled.
Initializing thread group data structures.
Creating threads...
Thread creation completed.


Opening target "/dev/sda11"


Image file pass 1/2.
/dev/sda11: 100.0% |************************************|   48.8 GB    00:00 ETA

Allocating work queues...
Work queues allocation complete. Building work queues...
Work queues built.  Workload:
pdf with header "%PDF" and footer "%EOF\x0d" --> **59 files**
Carving files from image.
Image file pass 2/2.
/dev/sda11: 100.0% |************************************|   48.8 GB    00:00 ETA

Processing of image file complete. 

Cleaning up...

```


I haven't quite worked out the correct odt header/footer 
this gave zero hits ... 
```

odt y 1000:10000000 \x50\x4b\x03\x04\x14\x0000\x08\x00\x00\x92\x51\xc8\x46\x5e\xc6\x32\x0c\x27\x00

```
but I'm taking a break now.

I google searched for "scalpel-2.0 odt" and found this example scalpel.conf

[https://github.com/machn1k/Scalpel-2.0/blob/master/conf/s_docs.conf](https://github.com/machn1k/Scalpel-2.0/blob/master/conf/s_docs.conf)

I copied only the line ...
```

[COLOR=#333333]ODT|ODP|OTT                         y    2500000    \x50\x4b\x03\x04[/COLOR]

```
into my scalpel.conf

Then started another test run ..

scalpel -c /etc/scalpel/scalpel.conf -o ~/scalpel_odt /dev/sda11

It would narrow down recovery if you set max size of your file.

---

### Post by CordeTheAwesome on 2015-12-28
Thanks guys. Looks like it should run properly now.

(Update in about 2 hours.)

It's finding way too man files. It's already at 204 GB- although I'm not sure if this is showing where in the filesystem it has parsed through or not. Anyways, it said it will return over 870,000 files. There are about 870 files with each about 1000 odt documents, all of which I checked so far are too corrupt too open. It won't let me delete them either. :o

---

### Post by dragonfly41 on 2015-12-29
I'm finding the same in my test run using the ODT signature. I get to the point where I've filled up my disk and I have to start deleting recovered files.
 In fact scalpel-2.0 abandons the session when there is no spare disk space left..

In the destination folder I get a series of folders with files with ext ODT|ODP| which cannot be open in LibreOffice.   So I manually changed the extension to *.odt and still it will not open.

I can however inspect hexcode contents any of these files using GHex hex editor.

The audit.txt file is also useful.

I'm going to continue trying to understand better the odt signatures.
There must be a way of limiting the number of recovered files since pdf file recovery was straight forward.

I did find a useful library of carving signatures here ..

[https://github.com/int0x80/anti-forensics/blob/master/scalpel.conf]("https://https://github.com/int0x80/anti-forensics/blob/master/scalpel.conf")

 [http://www.garykessler.net/software/index.html](http://www.garykessler.net/software/index.html)

download FileSigs (12/13/2015)

[http://www.garykessler.net/software/FileSigs_20151213.zip](http://www.garykessler.net/software/FileSigs_20151213.zip)

Perhaps in meantime you should clear out your recovery folder and try photorec.


[added note]
> 
[COLOR=#000000]It won't let me delete them either.[/COLOR]
You will probably need to delete recovered files using sudo mode.


Incidentally .. can you remember the name of your lostbook file .. some text which appears at top of your file near header?

---

### Post by CordeTheAwesome on 2015-12-29
I was able to delete the files using the following code:

sudo chown -R [username] [directory path]

However, at this point, I've decided to officially give up on this search. I greatly appreciate all the strenuous work you guys have put in to help me. In fact, I genuinely feel that in all my years this has been the most helpful forum I've come across. In addition, I definitely learned a lesson about the importance of backing up data. You have my sincere apologies for your time I most of took up and wasted. 

Thank you all!

---

### Post by dragonfly41 on 2015-12-29
Sorry it didn't work for you. Time was not wasted since forensic data recovery is always worth learning.

If you are into writing books take a look at Scrivener (there is a Linux version).

---

### Post by sudodus on 2015-12-30
+1

I'm sorry too, that it did not work to recover the lost book. But I want you to know, *CordeTheAwesome* and *dragonfly41*, that I really admire your many attempts to find a solution. I agree, time was not wasted since data recovery is always worth learning :-)

-o-

I found this link about other lost manuscripts.

[lost-manuscripts](http://www.theguardian.com/books/2009/jan/23/1000-novels-lost-manuscripts)

I had heard of Thomas Carlyle: The French Revolution

> Carlyle lent the manuscript of his most ambitious work, The French Revolution, to his friend John Stuart Mill for comment. One night soon after there was a knock on Carlyle's door. It was a distressed Mill, who told him that a maid had mistaken it for waste paper and burnt it. Carlyle had to rewrite it from scratch.

and found stories about nine other losts manuscripts too.

It has been said, that Thomas Carlyle's book is so great because it was rewritten from scratch :-)

---

### Post by Bucky Ball on 2015-12-30
Think of it this way: if you accidentally deleted a partition right now, you would know to stop using the drive for anything except data retrieval, boot up testdisk for the partition and/or photorec to retrive the files, you'd have the partition back up and the data retrieved in minutes ... :D (Well, a few minutes.)

It was the five month lag time that killed it I'd say, but time not wasted, well done all, I look forward to the re-write and enjoy the forums and OS. ;)

(When data is deleted, it is not really deleted. The system marks the space it is on as 'available for writing' and the data will remain until you write something over it. Consequently, if you delete something today or did a few days ago, there is a chance that space on the drive hasn't been re-written. The longer you use the drive, the more chance the 'deleted' spaces are going to get written over, obliterating the 'deleted' data that was residing there.)

---

### Post by oldfred on 2015-12-30
While with hard drives data is not deleted, SSD are quicker about deleting data. The trim command is clearing unused sectors. The standard trim from Ubuntu is once per week, so after a week, most deleted data will be gone.

I am running trim daily, but have system on SSD and most of my data on HDD. But if entire system on SSD or /home on SSD backup or immediately recovering deleted data is vital.

---

### Post by Bucky Ball on 2015-12-30
Thanks for that info, oldfred. Even more helpful as I have just chucked an SSD in this lappy, as you are aware. :)

---

