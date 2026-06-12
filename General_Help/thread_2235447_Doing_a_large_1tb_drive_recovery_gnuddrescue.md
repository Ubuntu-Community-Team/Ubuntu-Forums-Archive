---
title: "Doing a large 1tb drive recovery gnuddrescue"
date: 2014-07-21
forum: General Help
---

### Post by martinhudds on 2014-07-21
I'm currently doing a recovery of an NTFS 1tb HDD.  The drive had been dropped and wasnt mounting. 
I have followed the Ubuntu data recovery wiki pretty well and the recovery is underway with no errors so far. But after 2 weeks running its only recovered 25gb of a possible 500gb of data. So I have a few questions.
1 Will gnuddrescue stop/not recover empty part of the disk to the image? So 500gb of data results in a 500gb image, or will it speed up over empty part and still have a 1tb image.

2. I'm happy that I may have to use other recovery tools such as photorec, but is it possible to mount (using offset) a partially recovered partition? Doing this I would create a working copy of the image.

3 If there is a simpler way of getting the data off, ie mounting the drive using a means I haven't considered this may be faster so I'm open to ideas. I was very surprised gnuddrescue hasn't found errors so maybe less damage than originally feared.

Thanks for any advice. Really appreciate the support.
If I appear to have asked something already here or in the wiki, apologies, can't see for looking! 

Martin

---

### Post by dragonfly41 on 2014-07-21
Although I haven't had to recover a failed drive/partition for some time (and I haven't used gnuddrescue) I'll add my thoughts.

(1) Keeping 1TB of data in just one partition makes it more difficult to recover in event of crashes.  In your next configuration I would suggest breaking up your data into several smaller partitions (since you have to restart from the beginning of each partition if a long recovery session has to be interrupted e.g. power down).

(2) Have you considered making a clone of your 1TB NTFS partition onto a separate drive and then recovering data from the clone?

(3) You will need extra storage to actually save any recovered data.   Don't run for a long time and then find you can't then _save_ your recovered files into another formatted device.

(4) When recovering NTFS partition you could try Windows recovery tools (if you have access to Windows).

[http://www.forensicswiki.org/wiki/Tools:Data_Recovery](http://www.forensicswiki.org/wiki/Tools:Data_Recovery)

[http://www.stellarinfo.com/recover-windows-nt.htm](http://www.stellarinfo.com/recover-windows-nt.htm)

(5) Have you tried running testdisk on your failed NTFS partition?

---

### Post by martinhudds on 2014-07-21
Firstly thanks for the reply and thoughts,

> **dragonfly41 said:**
> Although I haven't had to recover a failed drive/partition for some time (and I haven't used gnuddrescue) I'll add my thoughts.

(1) Keeping 1TB of data in just one partition makes it more difficult to recover in event of crashes.  In your next configuration I would suggest breaking up your data into several smaller partitions (since you have to restart from the beginning of each partition if a long recovery session has to be interrupted e.g. power down).
Yes, agreed, this drive is as provided by a friend ( his data loss not mine!) This the default on the drive as bought. I hope I can resume the recovery should I need to stop, having used the log file features thankfully.

> (2) Have you considered making a clone of your 1TB NTFS partition onto a separate drive and then recovering data from the clone?
In a way I thought that was what I was doing, the slow read rate of ddrescue just causing the stress factor. What utility have you had success with? If it reads faster its worth a try.
> (3) You will need extra storage to actually save any recovered data.   Don't run for a long time and then find you can't then _save_ your recovered files into another formatted device. 
That's already taken care of, aforementioned friend provided a replacement 2tb HDD for the recovery.

> (4) When recovering NTFS partition you could try Windows recovery tools (if you have access to Windows).

He had already had a shot, and my stress factor goes skyward with the win8 interface but I may revisit this. The drive is present on the system just not in my computer 
> [http://www.forensicswiki.org/wiki/Tools:Data_Recovery](http://www.forensicswiki.org/wiki/Tools:Data_Recovery)

[http://www.stellarinfo.com/recover-windows-nt.htm](http://www.stellarinfo.com/recover-windows-nt.htm)

(5) Have you tried running testdisk on your failed NTFS partition?

No, originally I didn't want to cause any further damage. I intended to recover an image and work on that. Perhaps lack of errors so far means I can give this a shot.

Thanks for your input

Martin

---

### Post by dragonfly41 on 2014-07-21
> What utility have you had success with? If it reads faster its worth a try.

Clonezilla .. works on Linux and Windows I recollect.

[added note .. but note reference to UEFI]

from within Windows .. [URL="http://www.mattwharton.co.uk/2013/04/using-clonezilla-with-windows-8.html"]http://www.mattwharton.co.uk/2013/04/using-clonezilla-with-windows-8.html

[http://www.edugeek.net/forums/o-s-deployment/125590-cloning-windows-8-a.html](http://www.edugeek.net/forums/o-s-deployment/125590-cloning-windows-8-a.html)


[/URL]

---

### Post by Mark Phelps on 2014-07-21
In my own experience, Windows data recovery utilities do a better job of recovering files and folders from NTFS partitions.  A couple worth trying are RecoverMyFiles and Minitool Data Recovery.  Both are free to install and try out -- to see what they can find.  You have to go online and buy a license to do the actual data recovery.

---

### Post by dragonfly41 on 2014-07-21
+1
I have also used RecoverMyFiles with success in recovering Windows NTFS.

Another which has high recommendations is [https://www.grc.com/sr/spinrite.htm](https://www.grc.com/sr/spinrite.htm)

But SpinRite is pricey.   In fact all Windows commercial recovery tools are pricey.   

Make sure you have first tried simple (free) tools such as chkdsk to recover NTFS bad sectors.

---

### Post by martinhudds on 2014-07-21
Thanks for the top tips and ideas. I'll look into the options. I had heard of spinrite so again it may be an option. 
I'm reticent to stop a recovery in progress that does appear to be working, no errors as I mentioned before.

I am likely to try clonezilla. I have used this previously for backup. Noted on the UEFI points too.

Moving on from suggested utilities I'm keen for anyone who has had some experience mounting images created from gnuddrescue.  Focusing on Q2 in my original post. Anyone had joy mounting partial partitions/ partial recovery. Even if you're experience relates to ext or other FS. This is useful if I do stop the recovery to try to use something else. Even if I ditch what it has recovered later it is still a useful learning curve to follow. 


Thanks to all for the contributions so far.

Martin

---

### Post by dragonfly41 on 2014-07-21
More tips gleaned ...
If you have to restart gnuddrescue you should read how to monitor progress _before_ restarting a new gnuddrescue run ...

install pv and dcfldd through Ubuntu Software Centre

This article writes ..

> Note: you cannot use pv when you already started dd. 

> You can monitor the progress of dd without halting it by using the kill command. To see the progress of dd once it's running, open another terminal and enter: sudo kill -USR1 $(pgrep ^dd

[http://askubuntu.com/tags/dd/hot](http://askubuntu.com/tags/dd/hot)

And this article underlines the earlier advice above to first clone your failing drive before running gnuddrescue on the clone (not the original failing device).

[http://techmuck.blogspot.co.uk/2012/03/data-recovery-with-gnu-ddrescue.html](http://techmuck.blogspot.co.uk/2012/03/data-recovery-with-gnu-ddrescue.html)

I appreciate that this advice might be coming too late .. but if you restart .. then (a) clone first, (b) ddrescue from cloned partition.

---

