---
title: "Error: Disk write error - Input/output error, write fails"
date: 2008-01-03
forum: General Help
---

### Post by bossa on 2008-01-03
Hi All

Can someone please advise me . I'm quite new to Linux and I got this message in Azureus while downloading a Distro (Sabayon) of 4.22gb . The download had got to 3.83gb.
 
There is another thread that has a similar message in Azureus

[http://ubuntuforums.org/showthread.php?t=183553](http://ubuntuforums.org/showthread.php?t=183553) 

but the message ends with "flush fails" .I installed on to a disc that was previously XP and NTFS don't know if that has something to do with it.Surely there must be a way of downloading files bigger than 4gb using Linux

Oh yeah I am dual booting with Windows NTFS on a second drive

Any help will be much appreciated 
Thanks

---

### Post by joe.turion64x2 on 2008-01-03
Do you have the latest Ubuntu? If you are simply downloading to your home directory then it must be an ext3 partition which certainly allow to store files bigger than 4GiB. The previous format the drive hard doesn't matter as long as you created new partitions in its place.

Is there enought disk space available for the operation to complete?

Joe.

---

### Post by bossa on 2008-01-03
Hi Joe
 Ubuntu 7.10 Gutsy ,Azureus made a download folder in the Home folder . The whole 80 gig disk was used for this install and there is 62 gig space on the home folder

Should I just try and download the file again? there did not seem to be an option to re-start it, I did a recheck but it failed so in a tizz I deleted it!:oops: Just dont want to waste a load of time and bandwidth for it to fail again

---

### Post by joe.turion64x2 on 2008-01-03
> **bossa said:**
> Hi Joe
 Ubuntu 7.10 Gutsy ,Azureus made a download folder in the Home folder . The whole 80 gig disk was used for this install and there is 62 gig space on the home folder

Should I just try and download the file again? there did not seem to be an option to re-start it, I did a recheck but it failed so in a tizz I deleted it!:oops: Just dont want to waste a load of time and bandwidth for it to fail again
Being that the situation and before trying any drastic 'solution' retrying the download is worth a try.

EDIT: Just remembered I read somewhere that Linux fails to reclaim space from the Trash directory, and although it says you have X space available you can only use X-Trash. Have you put stuff in the Trash directory? If so completely delete it from there.

---

### Post by bossa on 2008-01-03
> **joe.turion64x2 said:**
> Being that the situation and before trying any drastic 'solution' retrying the download is worth a try.

EDIT: Just remembered I read somewhere that Linux fails to reclaim space from the Trash directory, and although it says you have X space available you can only use X-Trash. Have you put stuff in the Trash directory? If so completely delete it from there.

OK Joe 
Will try downloading again ....maybe I'm just being impatient . Yeah I have deleted everything in trash , comes from retrieving space all the time using relatively small Hard Drives . Spoiled myself the other day and got a 250 gig drive ...thats the second drive on this machine, with Vista :redface:...Saying that I have not used Windows for a few weeks now. Just trying as much as possible to stay with Linux...if I can.

Let you know how I go.

---

