---
title: "LibreOffice Stopped working after update"
date: 2014-06-22
forum: General Help
---

### Post by TedinOz on 2014-06-22
Following a whole series of updates from LibreOffice 4.2.4 to v 4.3.0, a couple of hours ago, I can no longer get LibreOffice to work. Trying to open a file of any type, I get the message that the file is corrupted and would I like LibreOffice to repair it. Clicking yes I am told that it cannot be repaired and that it an input/output error. Screenshots of the updates are attached, along with error messages. I am not sure how to find appropriate log file error reports or which ones might be needed, so if anyone is able to guide me it will be very much appreciated.
Looking at my synaptic, it seems I am able to force install an earlier version of LibreOffice (4.2.5) which I am reluctant to do without advice as is not the version that was updated.
Fortunately, all of my business files were within Dropbox which had previous synced to another (Linux Mint) machine and I am still able to access and work them. However, all other LibreOffice files were not part of my Dropbox and can no longer access them. I do have most of them in a recent Backup file and haven't tried yet to restore them as it simply seems that LibreOffice is no longer working...I can't even open a new blank sheet of any type.


Screenshots below....[IMG][[IMG]http://img837.imageshack.us/img837/5628/lr41.png[/IMG]]("http://img837.imageshack.us/i/lr41.png/") [[IMG]http://img850.imageshack.us/img850/2849/2p5e.png[/IMG]]("http://img850.imageshack.us/i/2p5e.png/") [[IMG]http://img834.imageshack.us/img834/6065/pkv7.png[/IMG]]("http://img834.imageshack.us/i/pkv7.png/") [[IMG]http://img819.imageshack.us/img819/4016/2c74.png[/IMG]]("http://img819.imageshack.us/i/2c74.png/") [[IMG]http://img843.imageshack.us/img843/2870/4uxb.png[/IMG]]("http://img843.imageshack.us/i/4uxb.png/")[/IMG]

As I am in a state of crisis about this, any help available will be so much appreciated. My OS is Ubuntu 12.04.4 LTS i686. Kernel is 3.2.0-64-generic-pae.

Thanks in advance.

---

### Post by SuperFreak on 2014-06-22
Did you install 4.2.4 from a PPA and then update it. Reason I ask is my version is 4.2.3 which came with my 14.04 install. Updating beyond what is in the Ubuntu repositories may lead to problems

---

### Post by TedinOz on 2014-06-22
> **SuperFreak said:**
> Did you install 4.2.4 from a PPA and then update it. Reason I ask is my version is 4.2.3 which came with my 14.04 install. Updating beyond what is in the Ubuntu repositories may lead to problems

 Yes I installed from PPA...I think it would have been this one... [http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu) precise main. It wouldn't have been 4.2.4 then (I think 4.0) and there have been multiple updates since then without problems. It was installed a long time ago...towards 12 months I would think? If it is as you say, do I have to revert to the native install and is there a way to do this?

Thank you for your interest and input.

---

### Post by TedinOz on 2014-06-22
Ok...it took me a while to get my head around it but based on the comment by Superfreak, I was forced to search and read extensively, to learn of the dangers referred to and to learn how to purge the offending PPA and attached version and reinstall the repository version. All of this I have done and (with great relief) all is working properly again. Clearly I have also learnt that warnings are not made without good reason and an old saying 'lead us not into temptation' should be observed here. Many thanks Superfreak :)

---

### Post by robin7 on 2014-06-23
Be sure to mark this SOLVED so others with a similar issue will learn what you did!  I definitely learned to avoid adding PPAs, especially on an "older" LTS version.  My vital applications are safely updated in the Ubuntu repositories.  Those times that I have gotten impatient and added a PPA were *usually* harmless, but occasionally disastrous!

---

