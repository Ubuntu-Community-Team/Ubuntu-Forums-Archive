---
title: "File Recovery Advice"
date: 2008-06-24
forum: General Help
---

### Post by darbid on 2008-06-24
I am almost a beginner.  And a total idiot.

I followed this thread [http://ubuntuforums.org/showthread.php?t=180668](http://ubuntuforums.org/showthread.php?t=180668)

but am posting here because I did not want to have it in the beginner thread.

so i have 

done a dd if=/somefile.img of=/dev/sdc1

sdc1 was a USB disk drive with many many files on it i did not want to delete.

What it did was remove the dev/scd1 USB drive and my mounting of /media/movie and then change it to /media/somefile as the new mount point.  The file system says UDF.

On reboot this comes up as a totally new mount and I can only see  the results of the above .img extraction.  (at least that worked)

so what has it done here, more importantly how can I get my files back.  Loosing them is not really an option.

---

### Post by Thanoulis on 2008-06-24
Sorry pal...:( Nothing can be done after a dd as far as i know...
If you need more info about the *dd* command, check this:
[Learn the dd command]("http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/")

---

### Post by darbid on 2008-06-24
Thanks for the reply.

Holy **** surely that cannot be.  In my mad rush to get these files back i have found all sorts of solutions for deleted files/folders and formated disks.  

What pisses me off is I go no warning of what this was going to do.

Please anyone...is there a way

---

### Post by darbid on 2008-06-24
As I settle down a little I realise that I have come accross a tool "dd-command" that is great for securing or DELETING data on a drive.

The question I have though is that what I did above took 10min to do.  The drive is 1TB there is no way it wrote over all the files in the drive.....it would take hours.  Plus I have read there is some "zero" function with dd that does this and not what I did.

So I am not giving up hope.  Although there is not much left.

---

### Post by aysiu on 2008-06-24
Try installing *testdisk* and running ```
photorec
``` See what you're able to recover.

---

### Post by darbid on 2008-06-30
I am glad to say that in my case most files can be recovered.

Especially if the files are small and common.

I had to go back to a windows box to do it but those data recovery programs found most of my files.  Obviously the 4gb that I wrote to the disk overwrote some files but the rest was still there.

I do say "most" as I had some large video files (about4gb) and these were only partially recovered. Basically as the dd command deletes any tables (eg MFT) on the disk (these are used by your OS to find files and or parts of files) you have to get your data recovery program to go through each sector of your drive and rebuild it.  Here you then have the problem that the less common files and the larger files are harder to recover by this method.

---

### Post by jimmy the saint on 2008-06-30
Well, I'm glad you were able to save the files, but I was going to suggest removing the drive and hooking it up to a windows box and using some recovery software on that end.  Unfortunately, I have found nothing in Linux that even begins to compare with what is available on the Windows side when it comes to file recovery.  I am sure there are a few, but not for the non-uber-linux-poweruser.

---

