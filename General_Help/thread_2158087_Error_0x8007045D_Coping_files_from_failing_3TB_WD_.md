---
title: "Error 0x8007045D: Coping files from failing 3TB WD Green HDD, I need a Linux terminal"
date: 2013-06-27
forum: General Help
---

### Post by 852258 on 2013-06-27
I was playing a video stored on my workstations internal 3TB WD Green hard-drive. This is how the problem started. The video playback froze about a minute into it. I tried playing several other media files stored on the same disk and all the videos consistently stopped playing after about a minute. I then tried a media file stored on a different 2TB hard-drive. It played without issue. I tried several other videos stored on the 2TB hard-drive and I had no problems with them at all.

I then tried copying a large 7GB file from the 3TB hard-drive to my desktop. It worked fine, then I tried copying a random folder full of videos containing about 13GB of media. As soon as I started I got the following error:

"
Copy File

An unexpected error is keeping you from copying the file. If you continue to receive this error, you can use the error code to search for help with this problem.

Error 0x8007045D: The requested could not be performed because of an I/O device error.
"

I tried coping several different folders on the 3TB hard-drive and they all gave me the same error trying to copy them.

I've temporarily disconnected the hard-drive in question, sealed it in a protective anti-static bag and put it in a safe place away from any heat sources. I just got back from the store and I purchased a new 3TB WD green hard-drive, same make and model within reason.

I've googled the problem and found some suggestions, possible causes, and trouble-shooting suggestions. Some people think this error has something to do with the File and Folder permissions getting screwed up or corrupted. To test this theory they recommended booting into safe-mode and attempting to copy some files from the hard-drive.

I tried copying files in safe mode but I received the same error message. Then just for good measure I booted into a ubuntu live cd to test. I got a similar error trying to copying files under Linux.

As far as I understand, Linux doesn't use the same file permissions as Windows does. Therefore, if the possible cause of the disrupted file permissions were the culprit then copying the files using Linux would have bypassed that altogether. Then when copying files that were created by Windows; Linux would ignore the permissions managed by Windows, just copy everything, if I'm correct about how it works.

I was helping a friend of mine, a while back, to update his MacBook to OSX 10.8 from 10.4 so he could use the Time Machine he bought for backups. So I needed to backup his files to a third hard-drive first and not the Time Machine from this MacBook’s internal hard-drive. There were problems copying some files because there was corruption. A lot of insignificant files, some random pictures, of nothing important but when the error appeared it would stop copying. So eventually I was able to copy all the files in the home folder at once with a terminal command I found online. It worked like a charm. Then I was able to re-install the newest OSX and copy his files back and configure his automatic backups through Time Machine instead.

I was wondering if there is something similar I can do in my situation. To keep copying the files, a little at a time, if need be; as the errors happen to get every file copied to the replacement hard-drive that I've purchased.

---

### Post by 852258 on 2013-06-28
bump - are we aloud to bump? I need to figure this out quickly. It will probably take 2- 4 days to backup my files after I figure out how to do that.

---

### Post by sandyd on 2013-06-28
You might want to look at testdisk/photorec for file recovery
Instructions for how to use photorec can be found at [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by 852258 on 2013-06-28
My drive is not formatted nor are my files deleted. I am able to play the files and skip through them. I believe all the files are intact. I believe the hard-drive's reading of that data has worn out or is failing. Your article doesn't seem to apply.

---

### Post by 852258 on 2013-06-28
bump - please help, this is urgent.

---

### Post by 852258 on 2013-06-29
bump

---

### Post by Mark Phelps on 2013-06-29
Bumping is to be limited to ONCE a day, not every few hours ...

Hate to tell you this, but I had three WD drives fail me last year in only a few months, and one was only a few months old.  Based on your comments, it sounds like the drive is failing -- as it looks like it may be encountering bad sectors when it is trying to read a file.

If you can connect a drive to a Windows PC, you can go to the WD site, download and install their drive checking utility -- and run that against the drive.  That will let you know if the drive is failing.

---

### Post by 852258 on 2013-06-29
I know for a fact the files aren't corrupt. I've been re-watching the files in question at full length over and over and they all stopped playing at the same time as the first one and at the same place. I think the head may be failing or the buffer. I believe everything on the disk is okay; it's the hardware that's used to get at that data which is effected I believe.

Sorry to hear about your bad luck. This 3TB disk is 1- 2 years old. So it lasted a little longer than yours. I’d really love to read about the statistic about different brands and models. If there is a website that collects those statistics.

Oh and sorry for the bumping. I did bump only once per day except for the last one that was within 13 hours of the one before it. I bumped it once before I went to bed. It's just urgent that I begin backing up files ASAP because I had work files on it. I can drag small files and single files one at a time and they copy file but I don't want to risk re-connecting the drive in question until I find the course of action that is safest and best.

---

### Post by oldfred on 2013-06-30
In Disks or Disk Utility click on the drive. It has Smart Status which will tell if drive is reporting errors. All I know is pass fail, but it has a lot of tests that it can run.

---

### Post by 852258 on 2013-06-30
While that's interesting, are the tests time consuming? Because this drive could be getting worse every second it's plugged-in. I don't want to connect it until I'm ready to backup all its content.

Also, could any of these test damage or affect the data? Or for that fact, could providing you a log of the test help you determine what method to use to copy my files? If not than the tests are counterproductive.

To be clear, I'm not interested in how or if the drive is failing. That part should be assumed because the goal is to retrieve and move those files as quickly as possible.

---

### Post by 852258 on 2013-07-02
bump

---

### Post by 852258 on 2013-07-06
bump

---

### Post by Habitual on 2013-07-06
[http://support.wdc.com/warranty/policy.asp#policy](http://support.wdc.com/warranty/policy.asp#policy)

---

