---
title: "Restoring Windows Vista backup files to Xubuntu 14.04"
date: 2015-07-27
forum: General Help
---

### Post by Mark_in_Hollywood on 2015-07-27
Yesterday, I helped my neighbor install Xubuntu on a Dell Inspiron E1405 laptop. I had to install a new disk drive as his old one failed (died) every 30 to 45 minutes.

Prior to the complete failure of the drive, I used the Windows Vista Backup to backup his pictures, resume, etc. Those files were put on a new external USB drive.

I have seen info on how to restore to Linux the (Microsoft) .bkf files, but Vista's are merely in a .zip format. Should be easy right? (Humpphhh!). The .bkf-s need the mftar to restore them. 

Can you help by pointing me to any URL or info on restoring from a Windows Vista (.zip) backup set to Linux? I've been netsearching this for 2 days (4 hours) now and am failing. The new drive is 500gig and even with 20 gig for / and 3 for swap there is sufficient disk space. It would not be a problem to make a directory, let me call it: vista-restored, and put all the files in it. I'll get that sorted out later.

Thanks in advance for taking the time to read this.

---

### Post by yancek on 2015-07-27
You haven't indicated what problem you are having if you have tried it.  The two links below should give you some info to start with.  What was used on windows to create the zip file(s)?

 [http://www.cyberciti.biz/tips/how-can-i-zipping-and-unzipping-files-under-linux.html](http://www.cyberciti.biz/tips/how-can-i-zipping-and-unzipping-files-under-linux.html)

[http://www.vbulletin.com/forum/forum/general/chit-chat/4301-can-you-unzip-a-winzip-file-on-a-linux-server](http://www.vbulletin.com/forum/forum/general/chit-chat/4301-can-you-unzip-a-winzip-file-on-a-linux-server)

---

### Post by Mark_in_Hollywood on 2015-07-27
> **yancek said:**
> You haven't indicated what problem you are having if you have tried it.  The two links below should give you some info to start with.  What was used on windows to create the zip file(s)?

 [http://www.cyberciti.biz/tips/how-can-i-zipping-and-unzipping-files-under-linux.html](http://www.cyberciti.biz/tips/how-can-i-zipping-and-unzipping-files-under-linux.html)

[http://www.vbulletin.com/forum/forum/general/chit-chat/4301-can-you-unzip-a-winzip-file-on-a-linux-server](http://www.vbulletin.com/forum/forum/general/chit-chat/4301-can-you-unzip-a-winzip-file-on-a-linux-server)

Cybercity returns a Error 404 (Not Found)!!!

and

vbulletin requires me to register as a member

What was used was the Windows Vista Backup and Restore Center. Thnx.

---

### Post by yancek on 2015-07-27
> Cybercity returns a Error 404 (Not Found)!!!

Interesting, I just clicked the link I posted and got right to the site.   You basically need to install zip/unzip as they are not installed by default. 

> sudo apt-get install zip unzip

There are also a number of examples which you can probably find at other sites with google if you can't access ciberciti for some reason.  The example below would unzip to the directory /media/vista-restored after you have created the directory.  Never used it for something this large myself and am not familiar with windows programs you mention, don't use windows myself.  Good luck.

> unzip pics.zip  -d /media/vista-restored

> vbulletin requires me to register as a member

The link is just a forum with three posts, very basic info to read.  Don't know why you would be asked to register unless you wanted to post?

---

### Post by Mark_in_Hollywood on 2015-07-28
MEH! Now Cybercity is now working. Go Figure!

I'm going try to restore the guys files today. I'll post here as to progress. Thanks.

---

