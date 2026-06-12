---
title: "copy to samba share results in more files on destination than source"
date: 2016-03-05
forum: General Help
---

### Post by sukelis on 2016-03-05
I've setup some samba shares on my new ubuntu server and have been in the process of copying files over to the server from the various other systems.  I usually collect the things I'm moving into a single folder (ie, a.xfer) on the source(windows) machine and copy that whole folder to the server/destination.  In windows explorer I then compare the folder properties to make sure they have the same number of folders and files and the same size (not the size on disk, which will vary between fs's).  Last night I started a transfer with a largish folder (68+GB) and when I compared the target and destination today - the DESTINATION has more files than the source!!!  2 folders on the destination have more files than on the source.  The folder count is the same, but the number of files and the size aren't.

This totally baffles me.  How can the server be adding files?  Does samba do something funky with expanding archives or something?  In one case I've narrowed the discrepancy down to a specific folder (a backup of my calibre library) but it has 390 sub-folders and over 1300 files.  

Has anyone ever seen a case where the copy has more files than the source?  Is there something specific I should be looking for?  A specific file or archive type that samba is known to expand?  I'm the only one using the network so it can't have been someone else's interference.

In setting up my samba server I pretty much followed the info in this thread [http://ubuntuforums.org/showthread.php?t=2313205](http://ubuntuforums.org/showthread.php?t=2313205).  I have been busy populating the server for 3 days and this is the first discrepancy where the server has gained files.  Usually it's something that windows hasn't copied that I have to track down and copy manually.

This just totally baffles me...

---

### Post by bab1 on 2016-03-05
> **sukelis said:**
> I've setup some samba shares on my new ubuntu server and have been in the process of copying files over to the server from the various other systems.  I usually collect the things I'm moving into a single folder (ie, a.xfer) on the source(windows) machine and copy that whole folder to the server/destination.  In windows explorer I then compare the folder properties to make sure they have the same number of folders and files and the same size (not the size on disk, which will vary between fs's).  Last night I started a transfer with a largish folder (68+GB) and when I compared the target and destination today - the DESTINATION has more files than the source!!!  2 folders on the destination have more files than on the source.  The folder count is the same, but the number of files and the size aren't.

This totally baffles me.  How can the server be adding files?  Does samba do something funky with expanding archives or something?  In one case I've narrowed the discrepancy down to a specific folder (a backup of my calibre library) but it has 390 sub-folders and over 1300 files.  

Has anyone ever seen a case where the copy has more files than the source?  Is there something specific I should be looking for?  A specific file or archive type that samba is known to expand?  I'm the only one using the network so it can't have been someone else's interference.

In setting up my samba server I pretty much followed the info in this thread [http://ubuntuforums.org/showthread.php?t=2313205](http://ubuntuforums.org/showthread.php?t=2313205).  I have been busy populating the server for 3 days and this is the first discrepancy where the server has gained files.  Usually it's something that windows hasn't copied that I have to track down and copy manually.

This just totally baffles me...
How did you transfer the data?  Did you use a GUI interface, or smbclient from the command line?  In the first case Samba is only concerned with mounting the remote file share to the local file system.  Whatever happened is a most likely a function of the transfer protocol used (Windows Explorer?).  If you used the later then the smbclient routines (sort of like FTP) may be the culprit.

I've never seen this happen.  I'm curious as to what really happened, but I'm just as much in the dark as you are at this point.  What happend with the "archive"?  Did it replicate itself?  Did it really extract all the contents into another folder?

---

### Post by nerdtron on 2016-03-05
If you use rysnc to copy files, by default it will not delete the files on the destination if it is not present on the source. So basically everytime you run rsync, the newer files will just be copied, the older ones which were already deleted from the source (but present on the destination) will be retained. Thus, older files will just keep piling up.

---

### Post by sukelis on 2016-03-05
Well, I can't figure it out but at this point I can say definitively that it has nothing to do with samba.  These weren't backups made with a backup utility just backup copies made using drag and drop between side by side windows explorer windows.  I tried a number of things to figure it out - just retrying the drag and drop, then doing it in batch using xcopy (windows), then I tried making the samba share into an actual mapped network drive and retried the batch again using the drive letter specification instead of the network \\ etc.  One folder had started off reporting 7 more files in the destination than the source, but when I copied it in batch it worked without issue and the source & destination matched exactly.  The other folder was/is reporting just 1 file more in the destination than the source.  And it's being damned stubborn about it, too.  I finally tried using a thumb drive bigger than the folder and it behaved the exact same way.

At that point I was getting pretty annoyed and finally sat down with my 2 windows and compared the source and destination, side by side and folder by folder.  But I could not find any actual discrepancy in the contents, even though the folder properties are still reporting 1 more file - and I always work with hidden and system files being shown, so it wasn't hidden (I even double-checked my settings).

Now that I know that it has nothing whatsoever to do with samba, I am going to force myself to drop it.  It was one thing when I was worried that there was a problem with my installation. If it's just windows being windows, then it's just one more reason to dump windows. 

But it's hard to let go of it because it just shouldn't **do **that!

---

