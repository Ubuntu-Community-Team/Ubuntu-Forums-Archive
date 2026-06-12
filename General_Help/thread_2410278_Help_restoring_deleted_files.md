---
title: "Help restoring deleted files"
date: 2019-01-13
forum: General Help
---

### Post by robnw on 2019-01-13
I was too careless and I deleted about 15 years of pictures from a folder on a secondary drive, not yet backed up sadly (backup was part of what I was getting to when I made this mistake).  

I've read about extundelete and have installed it but am having some difficulty using it.  I'm a novious ubuntu user.  I think I set up my file structure as ext3 or ext4, I don't remember.

I turned off my ubuntu computer though probably 2 or 3 hours went by (with little usage) before I discovered my huge problem.

From what I've read, I think I'm supposed to:


[LIST=1]
[*]start up the computer from a live cd/usb with extundelete installed
[*]don't mount the secondary drive
[*]presumably have access to a large enough other drive to store the recovered files
[*]run the command "extundelete --restore-directory <directory path> <partition>"
[/LIST]

However, when I gave this an initial try, I got a parsing error message.  Not sure why.  Possibly because the directory still existed (only the files were deleted)?

Also wondering: is there no way to restore in-place?  Are the restored files in the original subdirectory structure?

If it matters at all, the files were in a network share and deleted from another windows computer.

Any help greatly appreciated.  

Rob

---

### Post by monkeybrain20122 on 2019-01-13
How did you delete that folder? If you did right click > move to trash then just start Ubuntu, attach the second drive and check Trash, should find it there (if you check Trash without attaching the second drive you won't see it) then just restore it (Don't know what extundelete does, hopefully it didn't mess that up)

---

### Post by robnw on 2019-01-13
Right click, delete, from Windows.  I don't recall delesecting anything but I do recall something about "permanent" being flashed up on the window.  

I was, at the time, meaning to clean up another pictures folder.  Always backup.  Always double check.  Sigh.

Thank you for the tip, greatly appreciated.  I'll give that a try.  

Rob

---

### Post by monkeybrain20122 on 2019-01-13
OK, you deleted it with Windows, then  probably you should look up Windows tools, sorry I misunderstood, I thought you deleted it with Ubuntu.

---

### Post by robnw on 2019-01-13
no problem.  Thanks anyway.

---

### Post by MartyBuntu on 2019-01-14
You should absolutely stop using the drive until you run data rescue software on it.
I would recommend PhotoRec. 
[https://www.cgsecurity.org/wiki/PhotoRec](https://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by robnw on 2019-01-15
Thank you Marty.  The computer has been off since about 2 or 3 hours after I made the mistake and will stay off until I figure this out.

I'll take a look at photorec.  Someone else suggested testdisk, which I see it's related to.

Rob

---

### Post by dragonfly41 on 2019-01-15
An added note of advice.  If as it appears it is vital that you recover your deleted files then you would be advised to clone your drive image into another backup hard drive.  Research how to do this.  I have read horror stories of some tools being used incorrectly and wiping drives.  The general idea is that you can then work on the *cloned drive* to recover your files.  Put the original drive safely away.

You correctly deduce that you will also need some additional USB device into which you can *save *any recovered files.

The photorec (part of testdisk) tool is a well tried recovery tool. It does suffer the problem that you will recover files but you will lose all filenames.  Note that recovery sessions require the target drive to be unmounted.

Given that you have safely cloned the original drive you can try multiple recovery experiments. Some recovery processes might require hours of scanning perhaps overnight runs.  

Another tool I would try is R-Linux (for ext partitions) which runs on both Ubuntu and Windows. But do not run such tools in the same drive from which you are recovering files since you run the risk of overwriting any deleted files space in drive.

---

### Post by robnw on 2019-01-15
Thank you Dragonfly.  I'll go out and get an additional drive or two and keep the original safe for the time being.

---

### Post by robnw on 2019-01-15
Does anyone know .. 

From what I can tell, tools like extundelete, testdisk, photorec, etc., all create recovered files with generic names and I assume all in one flat directory.  I.e., the original file names generally can't be recovered nor can the original directory structure with the files included.

Rob

---

### Post by QIII on 2019-01-15
Hello!

That is the expected behavior of many of that sort of tools.  You may be faced with the prospect of tediously renaming every file.

Show me someone who says they've never done anything like this and I'll show you a liar.

You have learned the value of backups, so there is that silver lining.  It would have been an easier lesson had the damage been less.  Unfortunate, that.

---

### Post by dragonfly41 on 2019-01-15
In learning how to get started here is a [very dated tutorial]("https://lifehacker.com/5525534/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd") which illustrates what to expect with photorec.  
Note that the file names change.

There are other tools such as foremost. These require some knowledge of the internal metadata in files to be recovered.
One experiment might be to generate a photo image on a working OS as a template and then inspect its internals.
You will learn a lot if you approach this as a data forensics exercise.

I would continue to try as just one option [installing R-Linux]("https://www.r-studio.com/free-linux-recovery/Download.shtml") on your OS which is to be used to attempt recovery. 
Repeat .. not on the actual drive (preferably cloned drive) holding the deleted files.

[COLOR=#a52a2a][Later edit][/COLOR]
I will add another note. Be warned that when you start finding deleted files you may find many files which you intentionally deleted mixed with files you deleted in error.

---

### Post by robnw on 2019-01-15
Thanks QIII.  Lesson Learned.  Also - measure twice, cut once.

---

### Post by robnw on 2019-01-15
Thanks again Dragonfly.

---

### Post by QIII on 2019-01-15
> **robnw said:**
> Thanks QIII.  Lesson Learned.  Also - measure twice, cut once.

If you cut it too short, just keep cutting until it fits.

---

### Post by robnw on 2019-01-16
> **QIII said:**
> If you cut it too short, just keep cutting until it fits.

And when all else fails, use a chipper to destroy the evidence.

---

### Post by robnw on 2019-01-19
I now have my new drive to help with the restore and I've added it (physically) to my computer.  Am I correct that if I start up in Recovery Mode then all partions are mounted as read-only, so I won't further damage the original drive with the deleted photos?

My plan is to do the following - does this make reasonable sense?

1. Boot into Recover Mode
2. Mount the new drive as read-write and set up 2 partitions
3. Use DD to copy the original drive with the deleted photos to the first new partition
4. Test various recovery options on the new copied data into the 2nd partition

Rob

---

### Post by robnw on 2019-01-20
Just realized a flaw in my approach.

The original partition size is larger than the new harddrive I got (and therefore the new partition size is too small).  And I assume that DD can't know when it's run out of "real" data to copy.

So I guess I skip step 3 above and go straight to step 4 using the original drive.  

Rob

---

### Post by robnw on 2019-01-22
So, testdisk didn't work well for me.  Possibly because of the way I configured it, I don't know.  It did restore all (?) of the deleted directories (yay!) but very few of the deleted photos (about 800).  What it did restore all had their original directory & file names.

So I tried photorec and had a lot more success.  About 114K photos recovered.  Alas, all with generic directory and file names.  But this is a ton better than zero.

Now looking for a tool to organize them.

---

### Post by dragonfly41 on 2019-01-22
That is good news although I would continue trying to recover the other 600+ lost files.
Did you run tools as root user?
Did you try R-Linux?
Have you explored other forensic data recovery tools like foremost and scalpel?

Search in google "Ubuntu NEAR forensic data recovery".

I found this very, very old script used to organise recovered file types.
[https://www.howtoforge.com/data_recovery_from_accidently_deleted_files_or_crashed_drives_in_ubuntu](https://www.howtoforge.com/data_recovery_from_accidently_deleted_files_or_crashed_drives_in_ubuntu)

I would look at it as a template and bring it up to date. I have not tried it.

---

### Post by Impavidus on 2019-01-23
You wrote you're mostly dealing with pictures. Most jpeg pictures contain exif data, describing things like date and time when the picture was taken, sometimes the location (if the camera supports that), camera settings and maybe a caption, if you added one. The **exif** tool can read these data from the files. With some scripting you may be able to put the pictures in different directories depending on the creation date or something like that. That should help getting them sorted. I wouldn't be surprised if somebody already wrote a tool for that.

I've never had to recover pictures (or anything else) myself, but I use exif and some bash scripting to find specific pictures in my collection, based on caption.

---

### Post by dragonfly41 on 2019-01-23
exif is a good idea. I recollect now that I have[ Darktable]("https://libre-software.net/edit-image-metadata-on-linux/") installed which I see has a metadata editor.

---

### Post by robnw on 2019-01-23
@dragonfly41 - thanks for the suggestions.

---

### Post by robnw on 2019-01-23
Thanks @impavadus and @dragonfly41.

I found a couple of sites around using the exif data that I'll give a try.  I especially like this post 'cause it's based on the same problem I created:

[https://askubuntu.com/questions/404567/how-to-organize-sort-images-by-exif-image-data](https://askubuntu.com/questions/404567/how-to-organize-sort-images-by-exif-image-data)

---

### Post by robnw on 2019-01-24
I tried the jhead solution in the link above and it worked pretty well.  However, out about 1/3 of the jpg files (in one of my recovered directories) don't have exif data.  But for the other 2/3, jhead was able to rename the files and move them into a date-oriented folder structure.  Very cool.

A little more testing and some more recovery though still to do.

Rob

---

### Post by robnw on 2019-01-25
So was able to sort most of the jpg files into date-oriented folders and filenames using jhead.  It's a great tool.  I had a quick look at using exiftool but since I had the instructions already at hand for jhead, I went ahead with that one.

For any who care, I first copied all of the recovered files (jpg, mp4, and mov) into a single folder (they were spread across about 50 folders) then used the following command to sort them all: 

# for f in *.jpg; do sudo jhead -n%Y/%m/%d/%Y%m%d%H%M "$f"; done

Worked very nicely, created a bunch of folders in the format:

Year
  Month
     Day

Renamed the associated files to YYYYMMDDHHMM.jpg and moved them all into the appropriate subfolder

However, I also discovered that a bunch of the jpgs don't have exif info so I have a folder with a date from a few days ago with about 2000 pics that I need to manually go through.  But far better this than having to manually go through 100k photos.

Plus another bunch of jpgs that didn't get moved because of duplicate file names (jhead does a good attempt at trying to deal with this but I had many jpgs taken at the exact same time).  This should be easy to resolve with a 2nd jhead with a modified filename structure.

Rob

---

### Post by T.J. on 2019-01-25
> **QIII said:**
> Hello!

That is the expected behavior of many of that sort of tools.  You may be faced with the prospect of tediously renaming every file.

Show me someone who says they've never done anything like this and I'll show you a liar.

You have learned the value of backups, so there is that silver lining.  It would have been an easier lesson had the damage been less.  Unfortunate, that.


Amen, Qll.  I say the same.

Even the most experienced among us has lost data at some point.  The only protection is regular backups with multiple copies.  Do not depend on RAID to do it.

---

