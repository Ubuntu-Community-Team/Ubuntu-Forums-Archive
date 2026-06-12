---
title: "How to check integrity of files after big copy"
date: 2014-02-07
forum: General Help
---

### Post by Christodoulou_Marios on 2014-02-07
Hi everybody! I just finished copying some 200GB worth of films from a home server (NAS like box that is also my modem, it is the network provider box) to an 1TB external usb hard disk (3.5'' disk internal disk in a usb casing) that I have connected to my laptop (because I will change provider and I have to give them their box back). I accidentally dropped my hard disk on the floor by stepping on the power cable (about middle way through the copying process). The impact was light, no visible damage done, copying continued normally for some hours (i was doing this trough wi-fi) and no error messages. However, I would really like to check that indeed the files where copied well on my hard disk (regardless of the hard disk being dropped, but now i think i really should). I am not sure how to do this, I think I must use rsync or something similar. Please advice on command line tools not GUIs like Krusader. I can connect to my server via ftp. Thanks in advance!

---

### Post by 3rdalbum on 2014-02-08
Can you run any commands on the NAS box (i.e. does it have a Linux terminal you can access over SSH?)

If so, use the md5sum command on the files on your hard disk and record the results:

```
md5sum /media/Harddisk/Videos/* > sums.txt
```

Now SSH into the NAS box and run basically the same command to generate the MD5 sums for the original copies of the videos. Compare the "sums.txt" file on the NAS box with the one on your computer. If the video files differ in any way, their sums will be totally different. (you can compare the sums.txt files side-by-side by eye in Gedit, or use the 'diff' command to quickly show you any differences).

If you don't have SSH access to the NAS, if you tried the md5sum trick you'd basically be copying the video files to your computer again! You might as well just copy them all again to your hard disk, if you're in doubt.

I'd say that if you didn't get any error messages during the copy, that everything would be okay. Linux is very fussy about getting things right, and any errors during read or write will cause an Input/Output error message.

---

### Post by Bucky Ball on 2014-02-08
All of the above. I will be using the md5sum trick myself. 

Next time you could try something like Luckybackup which checks this and lets you know of any problems at completion of the job. There are other backup tools that will do the same. More efficient than drag and drop and also repeatable as you can save it as a backup job and run it as a regular backup in future and it will ONLY change/add anything to the backup that's been changed/added to the source, not re-backup everything.

Luckybackup is in the repositories. 

Just thought I'd throw that in. ;)

---

