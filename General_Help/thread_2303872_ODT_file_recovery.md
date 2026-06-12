---
title: "ODT file recovery"
date: 2015-11-22
forum: General Help
---

### Post by zamot.de on 2015-11-22
Hi to all of you,


I have a very specific problem and didn't find an answer for it. Though there are several threads on Internet that are related.
I have Libreoffice and it is configured to save the file each 15minutes and to do safe copies (they go to the backup profile folder, but some also to the tmp folder).
Yesterday I was working till the last minute and the computer crashed. I had to shutdown finally by force. 
The first thing I did was to reopen the Writer who proposed to recover the files, but the specific file I was working in prompted as unable to be recovered because of insufficient rights, but it became marked as good for recover only not with the green colour but yellow. Once the files I had open when the crash occurred where finally launched I had the shock to discover my most urgent file lost the last 5 pages! Very important and impossible to remake in the 7 days I still have to finish the work (very dense information and lots of notes that imply huge rereading). I lost my calm, save this file with another name and try to repeat the process. But the same. Strangely this file became exactly the same in my computer and in my usb key. Couldn't find anywhere one file renamed by the recovery process with "%%". In the backup folder there is only the one with 5 pages less. I'm checking the tmp folder but each time I try to open a document it blocks for hours before open it. It seems definitely lost. I'm not so sure if I was working with the file in the usb key or in the HD of the computer.
I tought to use scalpel but I don't seem to figure out how to recover the files.
I did sudo scalpel /dev/sde -b -o /media/sda1/scalpel-recovered-files, the terminal says 44 files carved but the folder is empty.

If someone could help me I would be grateful forever. I have to depose my thesis Friday and have yet to do other proofreading and write a conclusion.

Thanks in advance

---

### Post by bapoumba on 2015-11-22
Do you have any file saved posterior to the one with the 5 pages missing ?
Regarding your backup and temp folders, are these the ones specified in LO tools, under the path item ?
If so, once the file is closed, not sure there is much hope into recovering previous versions other than using the version feature when editing the file : [https://help.libreoffice.org/Common/Versions](https://help.libreoffice.org/Common/Versions)

Others should be able to help you out with testdisk, which I have never used..
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by oldfred on 2015-11-22
I have used photorec, but not scalpel. And if testdisk does show files that is best case. Scan tools like scalpel or photorec can take a long time.

 gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

With photorec it took overnight to scan drive on a relatively smaller drive. And I had to have another drive to copy data to. And it only recovered files by extensions, not full names. But I wanted my text files (notes of what I post) and I had a bit older backup. Photorec found all my text files and all the deleted copies. In some cases I had many copies of same file and had to do a lot of comparisons to original backup and grepping to find which .txt was which.  Some of the recovered deleted files were also corrupted. It tooks weeks to sort thru everything.

Saving to /tmp would be lost on a reboot as that is just temporary files.

---

### Post by zamot.de on 2015-11-22
Hi Bapoumba and OldFred,

thanks for the prompt answer.
The backup and temp files are those indicated in LO tools. I just saved the file with the lost 5 pages with a different name.
It seems I still have another instance of LO open but can't see where (it says that I should close it before open another one)
I have used testdisk in the pas to recover a whole partition. Thanks to remember. I checked the usb key with it and I could see a deleted older version but it was all. With the HD it is not possible (only a complete image of the disk). I recovered a lot of files with photorec that I'm opening now one by one, but photorec doesn't propose odt recovery just doc. I also launched foremost which completely occupied my free space (have o now). I could find for now one file that has 9 of the final 17 pages. It has a strange extention I never saw before .xs.
No, in the temp files there is still files from some months ago!

---

### Post by zamot.de on 2015-11-22
Quite strangely, all my favorites in Firefox and history disappeared also.

---

### Post by oldfred on 2015-11-22
Crashes often are caused by some sort of corruption or corruption is caused by a forced shut down.

If possible best to always remember elephants.
       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

And after a forced shut down fsck is often required.

---

### Post by bapoumba on 2015-11-23
> It seems I still have another instance of LO open but can't see where (it says that I should close it before open another one)
When you open a file, LO sets a lock on it so that another user cannot edit at the same time. Long answer, here for ex : [https://ask.libreoffice.org/en/question/51950/lockfilenameodt/](https://ask.libreoffice.org/en/question/51950/lockfilenameodt/)
If LO crashed with the file open, the lock remains. Delete the .lock file before opening LO again.

---

