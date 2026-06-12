---
title: "Help to Recover Video Files on External Drive (lost access after update OS version)"
date: 2017-03-19
forum: General Help
---

### Post by flyingsolo on 2017-03-19
I have digitized camcorder video on an external Seagate 2 T drive.
However, after upgrading from Ubuntu 14.04 to 16.04 last year, the drive is seen as "2.0 TB Volume" rather than the name it had (something like "Family Home video").
So no actual video files are accessible on it although nothing new has been written to the disk. 
The only listed files on it are as follows:
System Volume Information
   IndexerVolumeGuid
   WPSettings.dat
msdia80.dll

This is beyond my knowledge level! I'm wondering if there might be hope to recover the video files or not. I always have the brute force fix available of reimporting the video files from the camcorder which still functions.
I haven't any idea what I may have done wrong when upgrading the OS except that I should have just disconnected the external drive while doing the upgrade. It was a complicated update (for me, at least) b/c of the desktop being dual boot Win10 and Ubuntu.
Any suggestions or directions to similar old posts (I didn't find quite this issue) would be appreciated.

---

### Post by Mark Phelps on 2017-03-19
My guess is that you had the external driver running while using Win10 -- and that poses a SERIOUS issue unless you went to the trouble to disable Fast Startup in Win10 before you last shut it down -- and if you had done that, you likely would have mentioned it.

The Win10 Fast Startup causes all Windows filesystems to be hibernated when you shut down Win10.  This effectively blocks mounting those same filesystems in Linux, and if you force that mount, that will corrupt the Windows filesystem on the drive.

My suggestion, if you can still get into Win10, is to use one or more of the Windows-based data recovery apps listed below to see if you can retrieve any of the files and folders that were there:

Download and install this utility on a working PC: [http://www.majorgeeks.com/news/story](http://www.majorgeeks.com/news/story)

If that tool does not find what you need, an alternative is Recuva:  [http://www.piriform.com/recuva](http://www.piriform.com/recuva)
 
And, if that does not work well, the best tool out there is this one, but only the trial version is free:  [http://www.file-recovery.com/](http://www.file-recovery.com/)

Good Luck

---

### Post by flyingsolo on 2017-03-19
Thanks. Your link to majorgeeks doesn't work. Which of their data recovery tools was it? (7-data recovery?)

---

