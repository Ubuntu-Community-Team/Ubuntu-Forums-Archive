---
title: "Had a perfectly good ddrescue image .. and lost it."
date: 2015-02-19
forum: General Help
---

### Post by d_h2 on 2015-02-19
I recently ran ddrescue on a failing 450GB NTFS partition and it worked great. I was able to mount it, recover data, and so on.

Then, in an accidental stroke of the keyboard, managed to delete the image. I still have, however, the log file.

The original extraction took 8 days; I'm hoping that someone knows a combination of commands to tell ddrescue to re-run, using the logfile to skip the bad sectors and only fill in the good data as fast as possible.

I tried rerunning it like I did the first time (ddrescue --no-split /dev/sda4 /media/usb/backup.img /media/usb/backup.log) but that seems to have created a huge empty file, and is now back to trimming failed blocks.

Basically, I want to use the retry option only on good sectors.

-daniel

---

### Post by d_h2 on 2015-02-19
Found my own answer I think, at [http://unix.stackexchange.com/questions/60876/ddrescue-reread-only-good-sectors](http://unix.stackexchange.com/questions/60876/ddrescue-reread-only-good-sectors)

 > Thoroughly reread ddrescue manual and found out the following option:
[INDENT]   -m file
  --domain-logfile=file
      Restrict the rescue domain to the blocks marked as finished in the logfile *file*.  This is useful if the destination drive fails during the rescue.
 [/INDENT]
So the invocation of ddrescue would look something like this:
  # ddrescue -d -b 4096 -m sda1.log /dev/sda1 /mnt/sda1.img logfile2.log
     



---

