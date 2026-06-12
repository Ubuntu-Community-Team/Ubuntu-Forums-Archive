---
title: "Modified date not preserved on move/copy to NTFS partition"
date: 2008-03-02
forum: General Help
---

### Post by fsamuels on 2008-03-02
I have a number of disk drives on my system with different file systems. I still keep most of my data such as my photos, music and documents in my old My Documents directory on my Windows partition.

I have found that copying or moving any files to an NTFS partition changes the file modified date to be when it is copied or moved. This is not the expected behavior. Copying in Windows does not update the modified date and in Linux when the destination is on an ext3 or FAT32 partition the modified date is not changed

Does anyone know if there is a work around or know bug that is being worked on related to this? I rely on the file modified date for sorting and managing my photo collection but I can't copy them from my camera to an NFTS partition while in Linux without messing things up.

Thoughts? Ideas?

I saw another user may be experiencing [the same problem]("http://ubuntuforums.org/showthread.php?t=687503") but didn't get any responses.

---

### Post by Nzer24 on 2008-03-02
The fact that the operating systems are so different and the ntfs-3g driver is not perfect may just mean that some information is not preserved during copying. Not sure how you would work around that.

---

### Post by fsamuels on 2008-03-02
After much more searching it looks like this may just be a bug in ntfs-3g. I think it was fixed in release 1.1120 which is currently in the repository for the 8.04 release. Does anyone have a copy of Hardy Alpha with an NTFS partition running to see what happens when they copy a file in Nautilus to an NTFS partition from an ext3 partition? Copying using the command line never retains the modified date though. I find that even more strange. Anyway, I spent all day looking into this and [this is everything I found]("http://adventuresinswitching.blogspot.com/2008/03/copying-or-moving-files-to-ntfs.html").

---

### Post by rohan000 on 2008-05-16
This actually happens to me when copying between two ext3 partitions as well.

---

### Post by urshans on 2008-05-20
Too me as well - funny enough it only happens with 8.04! I did not have this problem with 7.04 and 7.10.

I remember though it happened in earlier versions, but I think I remember a method of changing it. But in 8.04 I don't find this anymore.


Apparently its is default in Linux/Unix to give a copy of a file a new date. But this is very annoying in everyday use, and to me as an information scientist, a copy of a file where nothing has been changed is not entitled to bear a new date.

If this does not going be repaired quickly, I will have to get back to 7.04...

Thanks and regards, Urs

---

### Post by fsamuels on 2008-05-20
My [previous problem]("http://adventuresinswitching.blogspot.com/2008/03/copying-or-moving-files-to-ntfs.html") that lead me to starting this thread was under 7.10, was limited to NFTS and was fixed in the backports repository.

This [new problem]("http://adventuresinswitching.blogspot.com/2008/05/file-modification-dates-changed-in.html") everyone is having where the modified date is changed regardless of the file system is new to 8.04. From what I can tell, the problem is due to the upgrade to GVFS. There is an [Ubuntu bug report]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/215499") and a [GNOME bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=515777") for it.

The only work around I know of now is to drop to a command line and use the -p switch with cp. Let's hope it gets fixed and in the 8.04 release.

---

### Post by fsamuels on 2008-05-20
You can try using gnome-commander too but it isn't much better than the command line in my opinion.

---

### Post by urshans on 2008-06-02
...but obviously nobody really cares about this subject. I have treturned to 7.04, but as other software with this release is not up to date (i.e. OpenOffice's compatibilty with MS Office 2007 files) I will have to return to 8.04 soon. I have tried out the GNOME Commander, it remembers me the old days of the Norton Commander (at his time a very good file manager!), so let's return to some nostalgia *big smile*

Urs

---

### Post by urshans on 2008-06-03
Dear all,

Hardy Heron 8.04 with GNOME Commander works fine, the original date is being preserved. So let's forget Nautilus for this purpose.... ;-)

Regards,Urs

---

### Post by rashly on 2008-06-05
Does anyone know when this bug will be fixed for 8.04? It's really annoying to have to use the command line every time I want to copy something. You would think that something as important as copying would be fixed right away.

---

### Post by urshans on 2008-06-08
I don't think it is ever going to be fixed. The responsible persons simply don't care or are too stupid to get the point. Certainly they don't evaluate us as customers.

When you follow the discussions on [https://bugs.launchpad.net/bugs/157396](https://bugs.launchpad.net/bugs/157396) you will loose hope.

Either switch to Mandriva or other Linux distribution. Or work with Thunar or GNOME Commander. But do *forget* about Nautilus...

---

### Post by Gallienus on 2008-07-02
I believe that this problem in Hardy has been solved in today's load of updates!

Losing the modified date was always a major issue for me. I was so fussy about preserving the modified dates that I developed the habit of archiving files before copying them, because then when I unarchived the files the correct dates were retained. But today I noticed that files copied in the normal way in Nautilus were finally keeping the correct modified date. Even copied folders kept the date, something that Windows doesn't do, as far as I recall.

This is a huge relief for me. :)

---

### Post by urshans on 2008-07-12
Yep, that's correct! I have been on vacation for three weeks - with no computing ;-) - and just installed the whole package of updates that have been sent since then. And now it works. As I have seen on the bug forum it is the libglib2.0-0 update that ist responsible for it.

Many thanks to whom ever!
:)
Urs

---

