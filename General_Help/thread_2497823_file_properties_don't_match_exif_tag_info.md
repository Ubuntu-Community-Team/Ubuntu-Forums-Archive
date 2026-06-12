---
title: "file properties don't match exif tag info"
date: 2024-05-19
forum: General Help
---

### Post by Keith_Beef on 2024-05-19
This is a problem I noticed a couple of months ago, and haven't given much attention until today.

I take pictures on a Canon EOS 100D, set to local time (UTC+1) and summer time (so currently UTC+2).

My computer is also set to the same timezone, synchronised with Network Time Protocol (NTP).

Today, at around 15h20 local time I took a few pictures. I took the SD card from the camera and put it in the computer.

[ATTACH=CONFIG]293790[/ATTACH]

How can that be right? It was 15h40 when I took that screenshot of the file browser.

I looked at the exif data in one of the image files:

```
$ exiftool -CreateDate _MG_6649.JPG
Create Date                     : 2024:05:19 15:23:06
```

```
$ stat _MG_6649.JPG
  File: _MG_6649.JPG
  Size: 3661701   	Blocks: 7168       IO Block: 131072 regular file
Device: 179,1	Inode: 18866       Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( 1000/xxxxxxxx)   Gid: ( 1000/xxxxxxxx)
Access: 2024-05-19 15:46:10.000000000 +0200
Modify: 2024-05-19 17:23:07.000000000 +0200
Change: 2024-05-19 17:23:07.000000000 +0200
 Birth: 2024-05-19 17:23:07.000000000 +0200
```

So the exif tag looks correct, but my computer is giving me times that are exactly two hours later...

Any ideas what's causing this?

---

### Post by TheFu on 2024-05-19
Use the EXIF data for when the photo was taken.
Use the file system data for when the file was copied to the computer.

That's how Linux/Unix works unless you use some special backup tool running as root to maintain timestamps.  It will be a fight, so best to get used to it and use the EXIF data.

---

### Post by Keith_Beef on 2024-05-20
I use EXIF data extensively, already, and classify photos by the value of the "CreateDate" tag, not by naively reading the timestamp of the files.

There is an important detail in my post, as shown in the screenshot, but not immediately visible unless you look at the filename of the screenshot, which is "Screenshot from 2024-05-19 15-40-45.jpg"... I didn't make this as clear in my original post as I should have.

I took the pictures shortly after 15h20 and took the screenshot at 15h40... and Linux is telling me that the files were last modified (i.e. written to the SD Card) shortly after 15h20: two hours ahead, which corresponds to UTC+2.

The card is advertised as 128GB, formatted in the camera so I expect it to be exFAT. 

Explaining the situation for the second time has pushed me to think a bit more about the problem.

The camera is set to UTC+2; I'm using exiftool to read the EXIF tag and I see what looks like the correct time of just after 15h20. But the computer is telling me mtime and ctime of just after 17h20 (along with atime of 15h46), **exactly two hours later**, which corresponds to the difference between UTC and my local timezone.

So maybe the camera is recording the value in something like ISO 8601 format, e.g. 2024-05-19T13:23:07+02:00 but the timestamp of the file on the SD Card is being written simply as 2024-05-19T15:23:07, by naively adding 2 hours to the time to account for the local time. The computer reads this value assumes it to be UTC and so adds two hours to the value when formatting it for presentation. 

So I suppose that what I really need to know is:
1. What value does the Canon camera write as mtime and ctime when writing the file to the SD Card?
2. How does the exFAT file system record these values?
3. How does Linux read mtime and ctime values from an exFAT file system?
4. How does exiftool reformat the value for presentation?

---

