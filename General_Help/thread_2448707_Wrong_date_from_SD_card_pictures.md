---
title: "Wrong date from SD card pictures"
date: 2020-08-12
forum: General Help
---

### Post by UBUminJ on 2020-08-12
I imported pictures today (August 12) from my SD card - and they are all wrongly dated (Nautilus shows September 12).
see the attached picture

Can I change something or is this a bug?

---

### Post by Dennis N on 2020-08-12
> **UBUminJ said:**
> I imported pictures today (August 12) from my SD card - and they are all wrongly dated (Nautilus shows September 12). see the attached picture Can I change something or is this a bug?
Is the metadata on the pictures correct? It matches the time settings for the camera. I have noticed for some time now that the 'modified date and time' shown in Files is derived from the image metadata, not when I actually saved the file. So if the camera has the wrong month set, then your photo's metadata would be incorrect, and the file date would be too.

---

### Post by oldfred on 2020-08-12
Import from my iPhone as been wrong for a while. 
I created a bash script to change date and another script to change HEIC files (which my wife's phone uses). I changed settings on my phone so it is jpg.   

I change to my photo folder with new files to run script, otherwise it would process every file in system which I do not want.  Some files do not work for unknown reason.

```
find . -type f \( -name "*.MOV" -o -name "*.heif" -o -name "*.JPG" -o -name "*.jpg" -o -name "*.jpeg" \) | while read PIC; do
    exiftool "-createdate>FileModifyDate" $PIC
    
done

```

# [https://unix.stackexchange.com/questions/89264/change-file-created-date-from-jpeg-exif-metadata](https://unix.stackexchange.com/questions/89264/change-file-created-date-from-jpeg-exif-metadata)
# [https://exiftool.org/](https://exiftool.org/)

---

### Post by HermanAB on 2020-08-13
Note that the simple Microsoft file system usually used on a SD card, has only one time stamp per file and it is usually set to when the file is written/copied.  So you don't really know when the file was created.

---

### Post by Dennis N on 2020-08-13
See attached image:

General Date and Time = correct local time photo was taken (camera is set manually to show local time)
Modified Date and Time = time stamp on the image file

Modified = General - 7

Subtracting 7 hrs would be correction from UTC to local time, but General time is local, not UTC.

---

### Post by UBUminJ on 2020-08-15
Some people didn't see the problem.

First of all that never happened before - my last Ubuntu used was 2019.04 - no problems. When I imported picture files into Nautilus, it always showed the correct date of the picture taken. When I took it on April 10 at 12:00 local time, Nautilus showed the transferred file as "file date April 10, 12:00 local time".
In Ubuntu 20.04, a picture taken at August 12 at 10:00 shows in Nautilus as September 12 at 20:07 file. 20:07 was the time of transferring the pictures. May I remind you that even if Nautilus would show the file creation on Ubuntu, it is wrong by 1 month.

It gets worse. I took photos today. Transferring them showed them as files on Nautilus with date stamp September 15. But the files from August 12, transferred again today, show up as October 12 files.

And YES, the metadata are correct. When I upload the files from Ubuntu onto my GDrive (via browser), they are sorted correctly with correct date and time.

---

### Post by srezz on 2020-09-03
Hi guys,
I'm having exactly the same problem. Did anyone solved it?

---

### Post by comunica2 on 2021-01-14
Exactly the same problem. Photo taken and written to SD on one date, file date is 1 month later (as if photo will be taken in the future). I definitely call this a bug. Ubuntu 20.04.1 LTS

---

