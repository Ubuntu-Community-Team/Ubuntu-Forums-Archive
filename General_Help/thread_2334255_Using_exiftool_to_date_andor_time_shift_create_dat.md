---
title: "Using exiftool to date and/or time shift create date of photos"
date: 2016-08-17
forum: General Help
---

### Post by cscj01 on 2016-08-17
I have Ubuntu 14.04.5 x64 using Gnome Flashback DE.  I had a malfunction on a series of photos I took that caused the wrong create date.  The date is off by +2 years, -2 months, and +1 day.  This is my first attempt at using exiftool, and I'm  wondering if someone could give me a straight forward command to accomplish that for a batch of photos?Misspelling

---

### Post by cscj01 on 2016-08-19
I have an example that shows me how to change the dates all in one direction, ie, increasing```
exiftool -AllDates+=5:10:2 DIR
``` which shows increasing the year by 5, the month by 10, and the day by 2.  However, I need to increase the year by 2, decrease the month by 2, and increase the day by 1.  I have yet to find any example that has both negative and positive values.  If the sign (+ or -) is in front, will I have to change each field (year, month, and day) with a separate command?  If so would those look something like```
exiftool -AllDates +=2 DIRPath
exiftool -AllDates -=:2 DIRPath
exiftool -AllDates +=::1 DIRPath

```Thanks.

---

### Post by Keith_Helms on 2016-08-20
Are all the dates in the Exif data screwed up, or just the create date?  If the Modify Date still has the correct original value, you could do this:
```
exiftool -CreateDate"<"ModifyDate *.JPG
```

That will set Create Date with the value from Modify Date.

---

### Post by cscj01 on 2016-08-20
> **Keith_Helms said:**
> Are all the dates in the Exif data screwed up, or just the create date?  If the Modify Date still has the correct original value, you could do this:
```
exiftool -CreateDate"<"ModifyDate *.JPG
```
b
That will set Create Date with the value from Modify Date.

Unfortunately, all the dates are wrong.  I have done no processing on them, so the Modify Date doesn't help here.  These were taken with a D810 and are NEF files.  I calculated the number of days the camera was off and used the following command on one image file```
exiftool 'AllDates +=0:731:0' PathtoFile
```This did not change anything.  I looked at all the EXIF data before and after, and there was no change.  Another odd thing is that the command indicating it was processing all images in that directory even though I specified only one file.  This is a funky tool to get straight.  There seems to be a forum at Queens University, but I can never get a connection there.  My browser just quits after 3-5 minutes, so I don't know anywhere to ask for help.metadata

---

### Post by cscj01 on 2016-08-20
I did find that I can modify the dates if I copy an image to a separate directory.  So far I have had to use a modification of the three commands I indicated in post #2, i.e.,```
exiftool '-AllDates +=2:0:0  0:0:0' DirPath
exiftool '-AllDates -=0:2:0  0:0:0' DirPath
exiftool '-AllDates +=0:0:1  0:0:0' DirPath
```Notice I also have to include the time figures and the other date figures.  In fact, I got the first and third commands combined by```
exiftool '-AllDates +=2:0:1  0:0:0' DirPath
```So I really only need two commands.  The next thing to solve is how I can do this for all the images in an entire directory.  I suppose I'll try it with two images copied into the test directory.  One baby step at a time, I suppose.

---

### Post by cscj01 on 2016-08-20
Okay, I have this working for all images in a directory.  The only problem now is to find out if my commands change anything other than DateTimeOriginal, CreateDate, and ModifyDate.

---

### Post by cscj01 on 2016-08-21
I have verified that the command```
exiftool -ext NEF 'AllDates +=2:0:1 0:0:0' DirPath
```only affects the original, create, and modify dates.  I have also used ```
exiftool -restore_original -ext NEF DirPath
```to restore the original metadata if a mistake is made in the write command.  Although I still do not know how to augment one part of the date (i.e., year) and decrement another (i.e., month), I can accomplish what I want with two commands where one augments the parts that require it (i.e., '-AllDates +=2:0:1  0:0:0') and the other decrements the parts that require it (i.e., '-AllDates -=0:1:0  0:0:0'.  I have also not found a way to affect only the date without adding the zero valued time changes.  With that, I will mark this thread solved.  Perhaps it can help someone encountering exiftool for the first time.  Since I assume that the primary reason for changing metadata is resetting dates and times, I believe this thread addresses the most frequent reason for using exiftool.  However, it is a very powerful tool, and I advise anyone who is using it for the first time to proceed with caution.

---

