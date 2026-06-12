---
title: "Video files won't play after update"
date: 2018-01-10
forum: General Help
---

### Post by bobnutfield on 2018-01-10
Hello

I am runnuing 16.04 on an old laptop and have hundreds of video files on it.  Never had a problem before, but today I updated (348mb) the system from Ubuntu and now no video files will play through any application.  The file starts to open and immediately shuts down and a request for an error report.

Anyone else experience this and does anyone know a way to fix it.  These files are very important to me.

Any help appreciated.

Bob

---

### Post by TheFu on 2018-01-10
If you patched today, it could be the Intel/AMD CPU fixes causing issues.  Boot from a LiveCD/flash drive and I bet everything is still there. 

If you can, restore from the backup you made prior to running the upgrades. I suspect for the next few weeks, having current backups will be important as these low-level patches are pushed out for all sorts of different things.

Which kernel is used?  According to a slashdot post, 4.4.x users are having issues.  **uname -a** will show the kernel.

And thank you for being patching ASAP and reporting issues.

BTW, did you check the log files?

---

### Post by bobnutfield on 2018-01-10
Thank you so much for your answer.  I used to be very fluent in linux, but it has been quite a long time since I have practised.  Uname gives me this:

4.4.0-109-generic #132-Ubuntu SMP Tue Jan 9 19:52:07 UTC 2018 i686 athlon i686 GNU/Linux

Indeed, I have that kernel.  I can live with it if it is going to be patched and fixed in the next few weeks.  None of the media players are working (VLC, Video, none of them.)    The files are still there and seem fine (thumbnails show up).  They just won't play on anything.

I discovered the problem when I was searching for a way to upload files from Ubuntu to my Seagate Personal Cloud.  Does't seem to be a way to do that either.  I have been using this laptop for about ten years and there are about 25GB worth of files I wanted to upload and wipe the drive on this computer to install something much lighter weight.  After ten years of upgrading release after release since 2008, this old girl is slowing to a crawl now, but still has a lot of life left.  Just needs a lightweight OS.

What is the command to read to log files?

Many thanks again,

Bob

---

### Post by TheFu on 2018-01-10
> **bobnutfield said:**
>  
What is the command to read to log files?

I would use **egrep** to search them for warnings and errors, but there are 50+ other methods. There's an ubuntu wiki page about log files that might be helpful. IDK, never read it.

---

