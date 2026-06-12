---
title: "Access Wubi Drives From XP"
date: 2007-06-28
forum: General Help
---

### Post by i&lt;3wubi on 2007-06-28
Sorry about reposting this but I think I posted in the wrong place.

Hi, I installed Wubi on Windows XP last week. Everything is working pretty well.

I would like to access Wubi's virtual drives while I am using XP. That way I can have access to Linux files without rebooting or if I make a boo-boo and didn't back-up a file like I was suppose to. What I found so far on this is:

[http://ubuntuforums.org/showthread.p...bi+disk+access](http://ubuntuforums.org/showthread.p...bi+disk+access)

However, the first step pertaining to Ext2, doesn't seem to work for me and install. The files that come archived with the Ext2Fsd zip seem to say "Just click the file of ext2fsd-0.30.exe. It will guide you for all. and writting on ext3 partition:". First off, no "ext2fsd-0.30.exe" file is included. Second, the download is supposedly for version 0.31a. Third, if I click on the setup.bat, it opens and then closes quickly.

Can anyone list a comprehensive How-To on how to properly achieve read/write access of Wubi drives from XP? I would greatly appreciate it. It would make Wubi even more wonderful.

Thanks

---

### Post by ago on 2007-06-28
The easiest way is to create a folder inside /home which is linked to a folder inside the windows file. Any file you put in there is visisble in windows. For execute the following code in Ubuntu

mkdir /media/host/wubi/shared
sudo ln -s /media/host/wubi/shared /home/shared

You should end up with /home/shared. Anything you put in there will be visible from windows under C:\wubi\shared.

---

### Post by i&lt;3wubi on 2007-06-28
Thanks for the prompt response.

I discovered I could move media, downloaded, etc., files a little after installing. I wanted to be able to read and write the files on the Wubi drives that I cannot move.

Since I haven't been able to get my dial-up modem or Beryl working, it is helpful for me to be able to study the files and system while in Windows XP on my working dial-up connection.

---

### Post by ago on 2007-06-28
Do one thing at the time, and with the debian the very first thing you have to sort out is networking. When you have notwork up, all the rest is much easier. Do a search on ubuntuforums for the make and model of your model.

---

### Post by instinctive on 2007-07-09
So I followed the instructions to create the shared folder and now I have no disk space available in my user folder under home. I have used up all 1.7GB in that folder but the shared folder has something like 27GB of free space. I was wondering if the shared folder that I have created has stolen the disk space from the user folder. This is quite annoying because I have decided I don't need the shared folder and I definitely need space in my folder.

PS. Thank you so much for this program. It is definitely the best way to test out Ubuntu when you still need Windows.
PPS. Sorry for posting this under the Wubi folder if this problem has nothing to do with Wubi.

---

### Post by instinctive on 2007-07-09
Well I now know that the 27GB of space in the shared folder is the amount of space I have left on my Windows install. Somehow my folder has found the space and now says it has over 1GB of space free. I have no idea why it just decided to find the space but I do know that something must have gone wrong with my ubuntu install because my firefox history was cleared and my 'menu editor' add-on was set back to default, as was the firefox display.

Anyway I'm happy now that I have free space.

---

### Post by ago on 2007-07-09
if you use the 'df' command you will see the free space of each partition. You have to move things out of /home/username and into /home/shared, but not folders that start with '.' 

Those contain configurations and settings and should stay in /home.

By the way the new minefield sets up /home/shared by default

---

