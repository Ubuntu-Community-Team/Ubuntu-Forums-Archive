---
title: "Is there a way to mark files for batch operations?"
date: 2014-03-27
forum: General Help
---

### Post by David_Wright on 2014-03-27
Hi.  I was wondering if there is a good way to do this:

What I want to do is browse through multiple folders of photos and in some (quick, easy) way "mark" the ones that are good enough to copy onto a usb key / other folder to take on holiday and show my folks.

My first thought was to assign them to a new group perhaps (although this would be a bit slow in file manager) - then a **find | grep | cp** to move them all, preferably in the same folder structure.

Anyone done this or got any good ideas?

*Background*: Total Linux newbie, Lubuntu, not terrified of the terminal.

---

### Post by TheFu on 2014-03-27
Use the shell to batch process them.
Or use multi-select with the CNTL key.

I'm actually working on a photo ranking tool to quickly set ranks **inside** the EXIF data. That can be used to ignore low-ranked photos for later processing.  Currently, I just add 'best' to the filename and process based on a filename regex.

---

### Post by whitesmith on 2014-03-27
Maybe we're not even on the same frequency, but here's an idea. If nothing is presently characterized, you could go through your collection in Nautilus shot by shot. When something rings the bell, copy it to your USB device (and maybe rename it somehow to avoid repetition of this mindless labor in the future [see previous response]). Good luck to you!

---

### Post by David_Wright on 2014-03-27
Thanks for the replies.  

**Whitesmith's** approach is the one I'm trying to avoid through laziness :~)

**TheFu's **idea is probably quicker than changing groups.

Maybe I should just edit my photos more diligently, but there's always ones that you want to keep "in case".

---

### Post by Vaphell on 2014-03-27
Nautilus has support for scripts which allows you to have custom options in the rmb context menu - very easy and straightforward. You would be able to select stuff, from the menu run a custom script looping through the paths to do what you want and call it a day.
I even wrote such a script in 5 minutes just for kicks.
Then there is nautilus-actions which expands on the idea with even more fancy stuff.

I also thought about using emblems to mark files and act on it in scripts, but of course gnome3 people in their infinite wisdom removed the gui and you have to cast some voodoo spells to get what used to be a 1click feature.

Lubuntu with its file manager make it a bit of pain though, i don't think such a feature is supported.

---

### Post by TheFu on 2014-03-27
> **David_Wright said:**
> Thanks for the replies.  

**Whitesmith's** approach is the one I'm trying to avoid through laziness :~)

**TheFu's **idea is probably quicker than changing groups.

Maybe I should just edit my photos more diligently, but there's always ones that you want to keep "in case".

Photo management is my life. [http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](http://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival) explains how I do it, but having an easier way ... 

My company is working on a solution for this stuff - quick ratings so you don't waste time on bad photos, merging photos from every device you have, making slide shows easily that can be exported, shared AND that work offline on **every device**, metadata completion, editing, correction, plus much more.  It isn't just about photos, but that is my personal itch.

BTW, the only photos I delete are really out of focus. Even a bad photo can help us relive an experience of a lifetime.

---

### Post by tgalati4 on 2014-03-27
Normally you would use a photo manager and tag the files "Christmas 2013", then search for that tag and perform a copy to a directory for flash drive.  However, there are several EXIF tools that you can use to tag files manually, then write a small script to search the EXIF data (again using one of the tools) to perform your copy operation.

eog-plugins - set of plugins for eog
exif - command-line utility to show EXIF information in JPEG files
exifprobe - Read metadata from digital pictures
exiftags - utility to read Exif tags from a digital camera JPEG file
exiftran - transform digital camera jpeg images
exiv2 - EXIF/IPTC metadata manipulation tool

---

### Post by spacemen12 on 2014-03-28
You can use shotwell.

Import the folder you want.

Scan through your photo, and use the star system. Press 1, 2, 3, 4, or 5. This will assign a number of start to each photo.

You can than look at your entire library, and filter for 3+ stars (option within shotwell), or whatever.

Ctrl+A, then export to your usb stick.


--------

You can also tag them, and you can filter, for only, e.g. trip, France, Friends, etc.

---

### Post by David_Wright on 2014-03-28
On the basis of earlier answers, I installed Shotwell last night and played with it briefly, but had not got as far as discovering **Spacemen12**'s method above - which looks perfect for what I want to do.

I read **TheFu's **blog, which has sensible advice more generally about image organisation and searched for a few of the command line programs that **tgalati4 **recommended - some useful information all round.

I'll mark this solved, and thanks again to everyone.

---

