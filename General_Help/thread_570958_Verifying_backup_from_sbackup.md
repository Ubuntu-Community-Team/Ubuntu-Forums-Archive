---
title: "Verifying backup from sbackup"
date: 2007-10-08
forum: General Help
---

### Post by lsutiger on 2007-10-08
I am planning on loading gutsy on my laptop as others have had great success with it using the same computer as mine...and it looks awesome!
But I did a backup with sbackup. Everything looks like it took. I set it up with the GUI to backup everything in my home folder through the configuration. I let it run and went do a few things. 

When I get back after about 45 mins, it is done. I was pretty amazed. My home folder is 26GB. I have a lot of music and videos. The backup file is only 4gb. Is compression at this rate really possible?

How can I verify that everything was backed up? I tried to open the tgz file, but I get an error stating something about an invalid EOF (end of file).

Thanx in advance!

---

### Post by lsutiger on 2007-10-08
OK I listed the files.tgz file and outputted to a file and it seems the backup stops when it gets to my music folder. But it does copy my videos, which are much larger.

I am at a lost of why this is.

---

### Post by lsutiger on 2007-10-10
ok I am not positive that it STOPS at the music folder, but my music folder is not listed in the file I created.

Anybody has any idea what is happening here?

---

### Post by ziggykg on 2007-10-20
This may be a bit late for you but if you're backing up to a FAT32 drive, e.g. a standard external USB drive, then the maximum file size you get on FAT32 is 4GB.  

Basically the backup EOFs when it gets to 4GB and it means that there's no guarantee that you'll be able to restore the back up fully.

---

### Post by lsutiger on 2007-10-20
Thanx for the reply, but the file system is ext3 for the backup drive.

---

### Post by rbmorse on 2007-10-20
Take a look at /etc/sbackup.conf

Some of the default excludes may not be what you want, and as I recall they don't show up in the configuration screen.

---

### Post by NoThanksM$ on 2007-11-23
Thank you for the FAT32 4GB limit reminder!  I couldn't figure out why my backup wasn't getting any bigger...guess it's been so long since I dealt with FAT32 that I completely forgot.

---

