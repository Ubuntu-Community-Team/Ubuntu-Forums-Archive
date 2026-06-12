---
title: "Multiple questions.."
date: 2006-11-05
forum: General Help
---

### Post by other guy on 2006-11-05
I thought it would be easier to ask all my questions in one thread.



1. I cannot get any of my home videos to play on my machine. It keeps displaying that the videos are text files. I have installed what I thought what would play them and changed what plays them. 
```
The filename "personal video.mpg" indicates that this file is of type "MPEG video". The contents of the file indicate that the file is of type "plain text document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "plain text document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 
```I picked movie player and then VLC to open it up. I have automatix installed. I just want to watch and show my personal videos.


2. Partition -  /media/hde1 240Gb RAID1 - on it's own controller. The drive that I have all my personal files on. Which in the fstab is listed as /media/hde1. I want it to be *fully* for my user. I read my tail off how to make it for my user. No matter what it still remians as root. How would I go about making it for my user. Any user in fact, long as it is not root. I want to be able to move files around and do what I want to them and not be so limited. It does not show when I do  *sudo nautilus*. One folder is under my user.. But I want the whole drive to be mine. I would like to be able to have more options for folders inside the drive.
```
# /dev/hda2
UUID=99533dce-c7f7-40f3-b291-5c4e208ae93a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=0f2c36dd-27cf-48f4-bb1d-c56fa49723ea /home           ext3    defaults        0       2
# /dev/hde1
UUID=c3df5aed-e3cf-4754-9273-beb4d1cfc28e /media/hde1     ext3    defaults       0       2
# /dev/hda1
UUID=158da563-fde3-4d3e-ac23-7dd89aeedc84 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
3. My internet under Windows was an alright speed of 8000/1000. Under Linux  I can only get a paltry 5000/780. (If I am lucky) This is one of my biggest issues. I am loosing money paying for a connection and only getting part of it. 

This is a stand alone machine. No other operating systems or on a wireless connections.

These issue I have read and read on trying to correct them. If I can't,  I must abandon Linux and go back to Windows. I want to keep using it, but if I can't correct these 3 issues. I have no choice. :( At least some cratfy work around for a semi-n00b.

---

### Post by jd65pl on 2006-11-05
Have you installed the codec for the file type you are trying to use? [See restricted formats.]("https://help.ubuntu.com/community/RestrictedFormats")

You may find you get more response if you post individual questions in the appropriate forums.

---

### Post by other guy on 2006-11-05
> **jd65pl said:**
> Have you installed the codec for the file type you are trying to use? [See restricted formats.]("https://help.ubuntu.com/community/RestrictedFormats")

You may find you get more response if you post individual questions in the appropriate forums.

I used automatix. It did work once.. then now it goes back to like when I installed the OS.



I figured one thread.. it can shed light on the issue as a whole. I considered single threads. Having all the issues in one spot can give an overall of a possible single event making my system act like a turd. If in a bit of time no resolution. I will create single threads, then cross link. I am hoping for some insight  as to what direction to read. Or at best.. a fix.

I am guessing.. It is the drive giving me the blues for the media. The internet, while important.. is a sperate issue. That can hold off. I want to get the bulk fixed first.. If along the way.. someone who knows spots  my thread.. w00t!

---

